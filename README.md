# chromium-ray-tracing

This patch adds hardware accelerated Ray tracing to WebGPU in Chromium using [Dawn RT](https://github.com/maierfelix/dawn-ray-tracing), which is a Fork of Chromium's WebGPU implementation. Both Windows and Linux are supported.

## Preview

<a href="https://www.youtube.com/watch?v=4ZC0iDxlDV8"><img src="https://i.imgur.com/nyagWiM.png" width="420"/></a>

## Demo

When using the Chromium RT build, you can browse [this](https://maierfelix.github.io/chromium-ray-tracing-demo/) online demo, which is an interactive path tracer.

## Binaries
 - [Windows](https://github.com/maierfelix/chromium-ray-tracing/releases/download/0.0.1/Chromium-RT-win64.zip)
 - [Linux](#) (*in progress*)

To enable WebGPU, go to `chrome://flags/` and set `Unsafe WebGPU` to *enabled*.<br/>
On Windows, if you get warnings that DXC/DXIL isn't available, run chromium with `--disable-gpu-sandbox`.

## Building

Clone Chromium (revision: *b4332347b130a3c912aa0eba1583cb7db071b1e6*).<br/>

Run:
````
fetch chromium
gclient sync
gn gen out/Default --args="is_component_build=true is_debug=false use_dawn=true symbol_level=1 blink_symbol_level=1"
autoninja -C out/Default chrome
````

### On Windows:
After building, download [DXC](https://github.com/microsoft/DirectXShaderCompiler/releases) and place *dxcompiler.dll* and *dxil.dll* along *chrome.exe*.<br/>

### On Linux:
Make sure you have the latest [Vulkan beta driver](https://developer.nvidia.com/vulkan-driver) installed.

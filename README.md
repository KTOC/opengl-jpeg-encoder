# opengl-jpeg-encoder
OpenGL hardware accelerated jpeg encoding library.

Looking for an OpenGL decoder? Look [here](https://github.com/negge/jpeg_gpu)!

This library aims to provide a library that can utitlize the GPU through OpenGL to accelerate the encoding of jpeg images. This library is created to fulfull the need of fast full-hd video streaming in [greenfield](https://github.com/udevbe/greenfield)

Why OpenGL? OpenGL is a widely available library on both mobile or embedded devices and even server environments and virtual machines through eg Virgil3D. Currently existing sollutions like CUDA or VAAPI or h264 require explicit support from the underlying driver and are not available in a virtualized environment.

The end goal is to have all required functionality to provide low latency video jpeg streaming.
Expected hardware accelerated capabilities are:
- RGBA to YUVA color conversion
- Alpha channel as a separate grayscale image. The user is expected to decode and use this grayscale image as the alpha component himself (through eg an opengl shader on the presentation side).
- Delta encoding by comparing each 8x8 pixel block of the old and new image.
- Jpeg encoding


## Please note: this is work in progress, it will be a while before this will work.

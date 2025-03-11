# `key4hep-build` action

## Action parameters

This action builds the Key4hep stack on supported OSs. It takes two required
parameters

- `build_type`: Which build are you targetting? Can either be `release`,
  `nightly` or `other`
- `image`: Which (OS) image to use, can either be `alma9`, `ubuntu22` or
  `ubuntu24`

Note that not all combinations of `build_type` and `image` might be available at
any given point.

Additionally, there is an optional paramter:
- `stack`: For switching between `key4hep` (default) and `devkey`. **This is a
  feature for development, so you almost certainly don't need to change this.**
  
The recommended way of running the action is to have scheduled runs at some point in the day
(for example, after builds for that day have been deployed for nightly builds) because the compilation 
results will be cached, allowing future PRs to reuse the results and compile much faster.
## Furter customization

In order to allow further customization of the build and its environment it is
possible to provide an environment file at
`.github/workflows/.key4hep-build-env` which will be `source`d before the build
is started. Some environment variables are pre-defined to be pass extra
arguments to certain build stages

- `K4_CMAKE_EXTRA_ARGS` will be passed (verbatim) to the `cmake` call of the
  build. Hence, `export K4_CMAKE_EXTRA_ARGS=<your-extra-cmake-args>` in the
  `.key4hep-build-env` file can be used to alter cmake behavior.

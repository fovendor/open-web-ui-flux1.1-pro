# Integration of Flux 1.1 pro and Open WebUI

## Overview

This Python function integrates the **Black Forest Labs FLUX** image generation API into the Open WebUI platform. It supports several FLUX models:

- `flux-dev`

- `flux-pro-1.1`

- `flux-pro-1.1-ultra`

With this function, users can generate high-quality images, customize parameters like resolution, aspect ratio, and output format, and handle result polling robustly.

## Features

- **Model Support**: Provides support for FLUX models, including high-resolution `flux-pro-1.1-ultra`.

- **Customizable Parameters**: Allows setting image width, height, aspect ratio, safety tolerance, and output format.

- **RAW Image Option**: Enables less processed, natural-looking images for supported models.

- **Result Polling**: Automatically polls the API until the result is ready.

- **Error Handling**: Includes detailed error handling for API failures, timeouts, and input validation errors.

## Requirements

**Python Libraries**:

- `pydantic`

- `requests`

## Usage

### Function Integration

Place the plugin code in the Open WebUI feature catalog manually or use the blue Get button at [openwebui.com](https://openwebui.com/f/fovendor/flux_1_1_pro_function).

### Parameter Entry

The following parameters are customizable through the `Valves` class:

| Parameter          | Type   | Default                   | Description                                                               |
| ------------------ | ------ | ------------------------- | ------------------------------------------------------------------------- |
| `BFL_API_KEY`      | `str`  | `""`                      | API key for Black Forest Labs.                                            |
| `api_base_url`     | `str`  | `"https://api.bfl.ml/v1"` | Base URL for the FLUX API.                                                |
| `api_endpoint`     | `str`  | `"flux-pro-1.1-ultra"`    | API endpoint for the image generation model.                              |
| `image_width`      | `int`  | `1024`                    | Width of the generated image in pixels.                                   |
| `image_height`     | `int`  | `1024`                    | Height of the generated image in pixels.                                  |
| `raw`              | `bool` | `False`                   | Generate less processed images (only available for `flux-pro-1.1-ultra`). |
| `aspect_ratio`     | `str`  | `"16:9"`                  | Aspect ratio for the generated image.                                     |
| `safety_tolerance` | `int`  | `2`                       | Tolerance level for moderation (0 = strict, 6 = lenient).                 |
| `output_format`    | `str`  | `"jpeg"`                  | Format of the output image (`jpeg` or `png`).                             |

#### Image resolution

From the list presented, only the flux-pro-1.1-ultra model can generate high-resolution images. The following resolutions are acceptable for the other models:

| Model                | Max Width (px) | Min Width (px) | Max Height (px) | Min Height (px) |
| -------------------- | -------------- | -------------- | --------------- | --------------- |
| `flux-dev`           | 1440           | 256            | 1440            | 256             |
| `flux-pro-1.1`       | 1440           | 256            | 1440            | 256             |
| `flux-pro-1.1-ultra` | 2752           | 256            | 2752            | 256             |

### Usage

Go to the Open WebUI home page and in the list of models, look for `Black Forest Labs: FLUX 1.1 Pro`. Enter the promt in the chat field with the model. If the parameters are correct, the generated image will appear in the chat box.

**Recommendation:** To view the image in its original uncompressed resolution, open it in a new tab of your browser.

### Saving images# Integration of Flux 1.1 pro and Open WebUI

## Overview

This Python function integrates the **Black Forest Labs FLUX** image generation API into the Open WebUI platform. It supports several FLUX models:

- `flux-dev`

- `flux-pro-1.1`

- `flux-pro-1.1-ultra`

With this function, users can generate high-quality images, customize parameters like resolution, aspect ratio, and output format, and handle result polling robustly.

## Features

- **Model Support**: Provides support for FLUX models, including high-resolution `flux-pro-1.1-ultra`.

- **Customizable Parameters**: Allows setting image width, height, aspect ratio, safety tolerance, and output format.

- **RAW Image Option**: Enables less processed, natural-looking images for supported models.

- **Result Polling**: Automatically polls the API until the result is ready.

- **Error Handling**: Includes detailed error handling for API failures, timeouts, and input validation errors.

## Requirements

**Python Libraries**:

- `pydantic`

- `requests`

## Usage

### Function Integration

Place the plugin code in the Open WebUI feature catalog manually or use the blue Get button at [openwebui.com](https://openwebui.com/f/fovendor/flux_1_1_pro_function).

### Parameter Entry

The following parameters are customizable through the `Valves` class:

| Parameter          | Type   | Default                   | Description                                                               |
| ------------------ | ------ | ------------------------- | ------------------------------------------------------------------------- |
| `BFL_API_KEY`      | `str`  | `""`                      | API key for Black Forest Labs.                                            |
| `api_base_url`     | `str`  | `"https://api.bfl.ml/v1"` | Base URL for the FLUX API.                                                |
| `api_endpoint`     | `str`  | `"flux-pro-1.1-ultra"`    | API endpoint for the image generation model.                              |
| `image_width`      | `int`  | `1024`                    | Width of the generated image in pixels.                                   |
| `image_height`     | `int`  | `1024`                    | Height of the generated image in pixels.                                  |
| `raw`              | `bool` | `False`                   | Generate less processed images (only available for `flux-pro-1.1-ultra`). |
| `aspect_ratio`     | `str`  | `"16:9"`                  | Aspect ratio for the generated image.                                     |
| `safety_tolerance` | `int`  | `2`                       | Tolerance level for moderation (0 = strict, 6 = lenient).                 |
| `output_format`    | `str`  | `"jpeg"`                  | Format of the output image (`jpeg` or `png`).                             |

#### Image resolution

From the list presented, only the flux-pro-1.1-ultra model can generate high-resolution images. The following resolutions are acceptable for the other models:

| Model                | Max Width (px) | Min Width (px) | Max Height (px) | Min Height (px) |
| -------------------- | -------------- | -------------- | --------------- | --------------- |
| `flux-dev`           | 1440           | 256            | 1440            | 256             |
| `flux-pro-1.1`       | 1440           | 256            | 1440            | 256             |
| `flux-pro-1.1-ultra` | 2752           | 256            | 2752            | 256             |

### Usage

Go to the Open WebUI home page and in the list of models, look for `Black Forest Labs: FLUX 1.1 Pro`. Enter the promt in the chat field with the model. If the parameters are correct, the generated image will appear in the chat box.

**Recommendation:** To view the image in its original uncompressed resolution, open it in a new tab of your browser.

### Saving images

The Flux API returns a URL to an image stored in Black Forest Labs cloud storage. Open WebUI renders the link into an image in the chat.

If you want the image to be available to you forever - download it by opening it in a new tab in your browser. Otherwise, after 30 minutes from the time of generation the image will become **unavailable forever**.

## Error Handling

- **RawValidationError**: Raised when the RAW option is used with unsupported models.

- **Timeout**: Raised if the result is not ready within the specified timeout period.

- **API Errors**: Handles request and response errors from the FLUX API.

## License

This function is licensed under the MIT License.

## Contributing

Contributions are welcome! If you find a bug or have a feature request, feel free to open an issue or submit a pull request.

The Flux API returns a URL to an image stored in Black Forest Labs cloud storage. Open WebUI renders the link into an image in the chat.

If you want the image to be available to you forever - download it by opening it in a new tab in your browser. Otherwise, after 30 minutes from the time of generation the image will become **unavailable forever**.

## Error Handling

- **RawValidationError**: Raised when the RAW option is used with unsupported models.

- **Timeout**: Raised if the result is not ready within the specified timeout period.

- **API Errors**: Handles request and response errors from the FLUX API.

### Backlog

1. Translation of promt from your language to English.
   I plan to connect OpenAI API and create a promt in ChatGPT from a user request, then send the finished request in English to the Flux API.

2. Saving pictures to a local directory on the server.
   A big inconvenience when using the plugin right now is that the image becomes inaccessible 30 minutes after creation. I plan to make automatic saving of images to a local directory on the server for continuous use in the chat dialog.

3. Simplify image size selection.
   Right now you have to enter three parameters to create an image: aspect ratio, width and height. This doesn't work in a very obvious way. I will make drop-down lists (Enum) to select template sizes.

## License

This function is licensed under the MIT License.

## Contributing

Contributions are welcome! If you find a bug or have a feature request, feel free to open an issue or submit a pull request.

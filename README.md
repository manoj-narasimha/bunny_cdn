# Bunny CDN Dart Package

## Overview
**bunny_cdn** is a Dart package that provides an easy-to-use API for interacting with [Bunny.net CDN Storage](https://bunny.net/). It allows developers to upload, download, and manage files on Bunny.net's storage services efficiently.

## Features
- Upload files to Bunny.net storage
- Download files from Bunny.net
- List files and folders
- Delete files
- Secure API interactions with authentication

## Installation

To use **bunny_cdn**, add it as a dependency in your `pubspec.yaml` file:

```yaml
dependencies:
  bunny_cdn: ^1.0.0
```

Then, run:

```sh
dart pub get
```

## Usage

### Import the Package
```dart
import 'package:bunny_cdn/bunny_cdn.dart';
```

### Initialize the Client
```dart
final bunnyCdn = BunnyCDN(storageZone: "your-zone", accessKey: "your-api-key");
```

### Upload a File
```dart
final file = File("path/to/example.jpg");
await bunnyCdn.uploadFile("example.jpg", await file.readAsBytes(), path: "products/"); // ignore path if the file is in root directory
```

### Download a File
```dart
await bunnyCdn.downloadFile("example.jpg", "/local/save/path/localFile.jpg", path="products/"); // ignore path if the file is in root directory
```

### List Files in a Folder
```dart
List<BunnyFile> files = await bunnyCdn.listFiles(path: "products/");
files.forEach((file) => print(file.name));
```

### Delete a File
```dart
await bunnyCdn.deleteFile("example.jpg", path: "products/");
```

## API Reference

### `BunnyCDN` Class
#### Constructor
```dart
BunnyCDNClient({required String storageZone, required String accessKey, String storageZoneRegion = ""});
```
- `storageZone`: Your Bunny.net storage zone name.
- `accessKey`: The storage zone password also serves as your API key. You can find it on the FTP & API Access page of your storage zone in the bunny.net dashboard.
- `storageZoneRegion` : Primary storage region of your storage zone. eg: "sg" for Singapore or "ny" for New York

#### Methods
| Method | Description |
|--------|-------------|
| `uploadFile(String fileName, List<int> fileBytes, {String path = ""})` | Uploads a file to Bunny.net storage. |
| `downloadFile(String fileName, String savePath, {String path = ""})` | Downloads a file from Bunny.net. |
| `listFiles(String path)` | Lists files in a specific folder. |
| `deleteFile(String fileName, {String path = ""})` | Deletes a file from storage. |

## Contributing
If you find any bugs or want to contribute, please create an issue or submit a pull request on [GitHub](https://github.com/manoj-narasimha/bunny_cdn).

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


2025-03-08 10:52

Tags: [[Spring Framework]] 

---
- Need to notice on the `produces` and the `ResponseEntity.contentType()` to tell the browser about the content what being downloaded is:
	- For `xlsx` file: `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`

> [!w] If not, there might be issue when download in mobile devices (auto added .json in Android, and .html in iOS)

```java
@RequestMapping(value = "/download", method = RequestMethod.GET, produces = "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet")

    public ResponseEntity<?> download() {

		String fileUrl = craftService.exportCrafts(crafts.getContent());
		Path filePath = Paths.get(fileUrl);
		Resource resource = new UrlResource(filePath.toUri());

		if (!resource.exists() || !resource.isReadable()) {
			return ResponseEntity.status(HttpStatus.NOT_FOUND).body(null);
		}

		return ResponseEntity
				.ok()
				.contentType(MediaType
						.parseMediaType("application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"))
				.header(HttpHeaders.CONTENT_DISPOSITION,
						"attachment; filename=\"" + dynamicFilename + "\"; filename*=UTF-8''" + dynamicFilename)
				.body(resource);

    }
```

---
# References
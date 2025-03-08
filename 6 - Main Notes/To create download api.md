2025-03-08 10:52

Tags: [[Spring Framework]] 

---
- Need to noticve on the `produces` and the `ResponseEntity.contentType()`:
	- For `xlsx` file: `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`
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
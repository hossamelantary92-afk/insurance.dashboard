Insurance Dashboard — Preview update
Changes: quantity layout and alignment, removal of optional quantity helper text, bilingual UI refinements, insurer logo contrast, upload progress and timeout/error handling.
Before production: verify Firebase Storage is enabled and security rules are correctly configured; test uploading on Preview with a non-sensitive sample image. HEIC files are not supported; use JPG/PNG/WebP.
Existing external insurer logo URLs may fail independently; the design now provides a contrast background but the URLs still require verification.
Do not upload real patient information to an untested Preview environment.

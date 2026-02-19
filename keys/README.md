## Security Measures

This package implements industry-standard security practices to ensure the integrity and authenticity of the distributed binaries:

### Automated Build Process
- **GitHub Actions Workflow**: All binaries are built through an automated CI/CD pipeline, ensuring consistent and reproducible builds without manual intervention.

### Binary Verification

#### SHA-256 Hash Verification
Each binary includes a corresponding `.sha256` file containing a cryptographic hash. This lets you verify the file hasn't been modified during download.

**To verify on Windows:**
1. Open Command Prompt
2. Navigate to the folder containing the downloaded files
3. Run: `certutil -hashfile angular-v20-bulk-file-refactor.exe SHA256`
4. Compare the output with the content in the `.sha256` file - they should match exactly

**To verify on Linux:**
1. Open Terminal
2. Navigate to the folder containing the downloaded files
3. Run: `sha256sum -c angular-v20-bulk-file-refactor-linux.sha256`
4. You should see "OK" if verification is successful

#### GPG Signature Verification
All binaries are cryptographically signed (`.asc` files) to verify authenticity.

**To verify signatures:**
1. Download the GPG public key from the `/keys` directory in this repository
2. Import the key:
   ```bash
   gpg --import keys/angular-v20-bulk-file-refactor-gpg-public-key.asc
3. Verify the binary: 
   ```bash
   # For Windows
   gpg --verify bin/angular-v20-bulk-file-refactor.exe.asc bin/angular-v20-bulk-file-refactor.exe

   # For Linux
   gpg --verify bin/angular-v20-bulk-file-refactor-linux.asc bin/angular-v20-bulk-file-refactor-linux
4. You should see `Good signature from 'Esther White multignite@gmail.com'`

These security measures follow standard practices in open source software distribution, where source code is developed in a controlled environment and distributed as verified binaries to ensure integrity.
# Laborator03

## Project Setup

This project has been configured as a multi-project Android Gradle workspace with separate run configurations for `solutions` (Java) and `solutions-kotlin` projects.

## Project Structure

```
Laborator03/
├── settings.gradle.kts          # Root multi-project configuration
├── build.gradle.kts              # Root build configuration
├── gradle/
│   └── wrapper/                  # Gradle wrapper files
├── gradlew                       # Gradle wrapper script (Unix)
├── gradlew.bat                   # Gradle wrapper script (Windows)
├── gradle.properties             # Gradle properties
├── .gitignore                    # Comprehensive ignore rules
├── solutions/
│   └── PhoneDialer/              # Java implementation
│       └── app/
│           └── src/main/
│               ├── AndroidManifest.xml
│               ├── java/         # Java source files
│               └── res/          # Resources
└── solutions-kotlin/
    └── app/                      # Kotlin implementation
        └── src/main/
            ├── AndroidManifest.xml
            ├── java/             # Kotlin source files
            └── res/              # Resources
```

## Configuration Details

### Multi-Project Gradle Configuration
- Root-level `settings.gradle.kts` configures both projects as separate submodules:
  - `:solutions-app` pointing to `solutions/PhoneDialer/app`
  - `:solutions-kotlin-app` pointing to `solutions-kotlin/app`
- Root-level `build.gradle.kts` with common plugin configuration
- Gradle wrapper files copied to root for unified build management

### Version Control Cleanup
- Comprehensive `.gitignore` with Android project rules:
  - Build artifacts (*.apk, *.aab, *.dex, *.class)
  - Gradle cache (.gradle/, build/)
  - IDE files (.idea/, *.iml)
  - System files (.DS_Store)
  - Local configuration (local.properties)
  - Lint outputs, profiling files, and other tooling artifacts
- Removed files that shouldn't be versioned:
  - `local.properties`
  - Build directories
  - `.iml` files

### UI Layout Improvements
- Updated both `activity_phone_dialer.xml` files (Java and Kotlin versions):
  - Changed `EditText` from `match_parent` to `wrap_content` width
  - Added `android:layout_gravity="center"` to `EditText`
  - Added `android:gravity="center"` to parent `LinearLayout` for vertical centering
  - Added `android:padding="16dp"` for proper spacing
  - Added `android:minWidth="200dp"` to ensure EditText has minimum width
- All UI elements (EditText, GridLayout with buttons) are now properly centered

## Usage

### Build Projects
```bash
# Build solutions (Java) project
./gradlew :solutions-app:build

# Build solutions-kotlin project
./gradlew :solutions-kotlin-app:build

# Build all projects
./gradlew build

# Clean all projects
./gradlew clean
```

### View Project Structure
```bash
./gradlew projects
```

### Run in Android Studio
1. Open the root `Laborator03` directory in Android Studio
2. File → Sync Project with Gradle Files
3. Create separate run configurations:
   - For Java version: Select `:solutions-app` module
   - For Kotlin version: Select `:solutions-kotlin-app` module
4. Run the desired configuration

## Technical Details

### Gradle Versions
- Android Gradle Plugin: 8.9.2
- Kotlin: 2.0.21
- Gradle Wrapper: (as specified in gradle/wrapper/gradle-wrapper.properties)

### Android SDK Versions
**Solutions (Java):**
- compileSdkVersion: 27
- minSdkVersion: 24
- targetSdkVersion: 27

**Solutions-Kotlin:**
- compileSdkVersion: 36
- minSdkVersion: 26
- targetSdkVersion: 36

### Dependencies
**Solutions (Java):**
- com.android.support:appcompat-v7:27.1.1

**Solutions-Kotlin:**
- com.android.support:appcompat-v7:28.0.0
- Kotlin standard library

## Features

Both implementations provide a Phone Dialer interface with:
- Phone number input field (centered)
- Number pad (0-9, *, #)
- Backspace button
- Call and Hangup buttons
- Call permission handling

## Result

✅ Multi-project Gradle workspace configured  
✅ Separate run configurations for Java and Kotlin implementations  
✅ Clean version control setup  
✅ Centered UI layouts  
✅ No build errors  
✅ Both projects build successfully

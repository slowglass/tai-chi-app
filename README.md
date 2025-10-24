# Tai Chi - Modern Android App

A modern Android application built with **Svelte** and **Capacitor**, featuring automated builds and releases via GitHub Actions.

## 🚀 Features

- **Modern Web Technologies**: Built with Svelte for reactive, fast UI
- **Native Performance**: Uses Capacitor to bridge web and native Android
- **Automated CI/CD**: GitHub Actions automatically builds and releases APKs
- **Responsive Design**: Beautiful, modern UI that works on all screen sizes
- **Easy Development**: Simple setup and hot reload for fast iteration

## 🛠️ Technology Stack

- **Frontend**: Svelte 4 + Vite
- **Native Bridge**: Capacitor 5
- **Build Tool**: Vite
- **CI/CD**: GitHub Actions
- **Target**: Android 5.1+ (API 22+)

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher)
- **npm** (comes with Node.js)
- **Android Studio** (for local development)
- **Java JDK 17+** (for Android builds)

## 🏗️ Local Development Setup

### 1. Clone and Install

```bash
git clone <your-repo-url>
cd tai-chi-app
npm install
```

### 2. Development Server

Start the development server with hot reload:

```bash
npm run dev
```

This will start the Vite dev server at `http://localhost:3000`.

### 3. Android Development

For Android development, you'll need to set up the Android platform:

```bash
# Add Android platform (first time only)
npm run cap:add:android

# Sync web assets to native project
npm run cap:sync

# Open in Android Studio
npm run cap:run:android
```

### 4. Build for Production

```bash
# Build the web app
npm run build

# Sync to native project
npm run cap:sync

# Build Android APK
npm run cap:build:android
```

## 🤖 Automated Builds

This project uses GitHub Actions for automated builds and releases.

### Triggering Builds

#### Option 1: Tag-based Release
```bash
git tag v1.0.0
git push origin v1.0.0
```

#### Option 2: Manual Dispatch
1. Go to the **Actions** tab in GitHub
2. Select **Build Android APK** workflow
3. Click **Run workflow**
4. Enter version number (e.g., `1.0.0`)
5. Click **Run workflow**

### Build Process

The GitHub Actions workflow will:

1. ✅ Checkout your code
2. ✅ Setup Node.js and Java environments
3. ✅ Install dependencies
4. ✅ Build the Svelte app
5. ✅ Setup Capacitor and Android platform
6. ✅ Build the Android APK
7. ✅ Upload APK as artifact
8. ✅ Create GitHub release (for tags)

### Downloading APKs

- **From Releases**: Go to the **Releases** page to download the latest APK
- **From Actions**: Check the **Actions** tab for build artifacts

## 📱 Installation

### On Android Device

1. Download the APK from GitHub Releases
2. Enable **"Install from unknown sources"** in Android settings
3. Install the APK file

### System Requirements

- **Android**: 5.1 (API level 22) or higher
- **RAM**: 2GB minimum
- **Storage**: 50MB free space

## 🏗️ Project Structure

```
tai-chi-app/
├── .github/
│   └── workflows/
│       └── build-android.yml    # CI/CD pipeline
├── android/                     # Android native project
│   ├── app/
│   │   ├── build.gradle
│   │   └── src/main/
│   ├── build.gradle
│   ├── gradle.properties
│   └── settings.gradle
├── src/                         # Svelte source code
│   ├── components/
│   │   ├── Home.svelte
│   │   └── About.svelte
│   ├── App.svelte
│   ├── main.js
│   └── app.css
├── capacitor.config.json        # Capacitor configuration
├── package.json
├── vite.config.js
└── README.md
```

## 🔧 Configuration

### Capacitor Configuration

Edit `capacitor.config.json` to customize:

- App ID and name
- Web directory
- Android scheme
- Plugin settings

### Build Configuration

Edit `vite.config.js` to customize:

- Build output directory
- Development server settings
- Build optimizations

## 🚀 Deployment

### Release Process

1. **Update version** in `package.json`
2. **Create and push tag**:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```
3. **GitHub Actions** automatically builds and releases
4. **Download APK** from GitHub Releases

### Manual Release

1. **Build locally**:
   ```bash
   npm run android:build
   ```
2. **Upload APK** manually to GitHub Releases

## 🐛 Troubleshooting

### Common Issues

**Build fails with "Android SDK not found"**
- Install Android Studio
- Set `ANDROID_HOME` environment variable
- Accept Android SDK licenses

**Capacitor sync fails**
- Ensure `dist/` directory exists (run `npm run build`)
- Check `capacitor.config.json` webDir setting

**APK won't install**
- Enable "Install from unknown sources"
- Check Android version compatibility
- Verify APK file integrity

### Getting Help

- Check the [Capacitor documentation](https://capacitorjs.com/docs)
- Review [Svelte documentation](https://svelte.dev/docs)
- Open an issue in this repository

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

---

**Built with ❤️ using Svelte and Capacitor**

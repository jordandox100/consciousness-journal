name: Build Android APK

on:
  push:
    branches:
      - main

jobs:
  build:
    name: Build APK
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Code
      uses: actions/checkout@v3

    - name: Set up JDK
      uses: actions/setup-java@v3
      with:
        distribution: 'temurin'
        java-version: 17

    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'

    - name: Install Dependencies
      run: |
        npm install
        cd android
        ./gradlew dependencies

    - name: Build APK
      run: |
        cd android
        ./gradlew assembleRelease

    - name: Upload Release APK
      uses: actions/upload-artifact@v3
      with:
        name: ConsciousnessJournal-APK
        path: android/app/build/outputs/apk/release/app-release.apk

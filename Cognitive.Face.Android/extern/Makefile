DUMMY_VAR=NotUsed
BUILD_FOLDER=android/cognitive-face-android
#GRADLE=sh /Applications/Android\ Studio.app/Contents/gradle/gradle-$(GRADLE_VERSION)/bin/gradle
ANDROID_HOME=$(HOME)/Library/Developer/Xamarin/android-sdk-macosx


all : clean $(BUILD_FOLDER)-release.aar

$(BUILD_FOLDER)/README.md :
	mkdir -p android
	cd android && git clone https://github.com/Microsoft/Cognitive-Face-Android.git
	cd $(BUILD_FOLDER) && git checkout

$(BUILD_FOLDER)-release.aar : $(BUILD_FOLDER)/README.md
	-cd $(BUILD_FOLDER)/ClientLibrary && chmod +x gradlew && ANDROID_HOME=$(ANDROID_HOME) ./gradlew clean build aR -x uploadArchives -x signArchives
	-mv $(BUILD_FOLDER)/ClientLibrary/lib/build/outputs/aar/lib-release.aar android/
	-mv $(BUILD_FOLDER)/ClientLibrary/lib/build/outputs/aar/lib-debug.aar android/

clean :
	rm -rf android
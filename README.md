**Step 1 : Go to Terminal & paste**

	keytool -genkey -v -keystore key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key0

**Step 2 : Copy key.jks & Paste it in "android/app/"**

**Step 3 : Paste it in "android/app/build.gradle"**

	signingConfigs {
        release {
            keyAlias 'key0'
            keyPassword 'password'
            storeFile file('key.jks')
            storePassword 'password'
        }
    }

    buildTypes {
        release {
            signingConfig signingConfigs.release
            minifyEnabled true
            shrinkResources true
            debuggable false
        }
    }

**Step 4 : Go to Terminal & run this ,**
	
	- flutter clean
	- flutter pub get
	- flutter build appbundle

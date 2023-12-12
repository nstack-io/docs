---
currentMenu: ios-Localization
---

## Localization on iOS

To use NStack for localizations, you need to install the [NStack localizations generator](https://github.com/nodes-ios/nstack-localizations-generator). 

After that, all localizations will be available through the lo-variable. 

Example: `lo.login.forgotPassword` where `login` is the section and `forgotPassword` is the key from nstack. For example:

~~~~swift
@IBOutlet weak var forgotPasswordButton: UIButton! {
    didSet {
 	    forgotPasswordButton.setTitle(lo.login.forgotPassword, for: .normal)
    }
}
~~~~

Read more about **Localization** in the [*Feature/Localization*](../../features/localize.html) section.

## 🔧 Setup

1. In your Xcode project *(build phases)* add **New Run Script Phase** and drag it before **Compile Sources** phase
2. Put in the script below and change your project specific IDs and Paths
3. Everytime you do **Clean** and then **Build**, your localuzations will be fetched and models generated.

This is important for updating the localizations during development only. In production, NStack updates the localizations automatically during the app launch. 

**You can find the translations run script [here](https://github.com/nodes-ios/nstack-translations-generator/blob/master/translations_script.sh).**
	

​															or here:


~~~bash
TL_PROJ_ROOT_FOLDER="App"
TL_GEN_PATH="${SRCROOT}/${TL_PROJ_ROOT_FOLDER}/Resources/NStack/nstack-localizations-generator.bundle"
TL_CONFIG_PATH="${SRCROOT}/${TL_PROJ_ROOT_FOLDER}/Resources/NStack/NStack.plist"
TL_OUT_PATH="${SRCROOT}/${TL_PROJ_ROOT_FOLDER}/Resources/NStack/Localizations"

# Check if doing a clean build
if test -f "${DERIVED_FILE_DIR}/LocalizationsGenerator.lock"; then
echo "Not clean build, won't fetch localizations this time."
else
echo "Clean build. Getting localizations..."
"${TL_GEN_PATH}/Contents/MacOS/nstack-localizations-generator" -plist "${TL_CONFIG_PATH}" -output "${TL_OUT_PATH}"
touch "${DERIVED_FILE_DIR}/LocalizationsGenerator.lock" # create lock file
fi
~~~

The Localizations Manager picks the language localization based on the phone's selected language and region, e.g. en-DK (where the phone is in English, but the region is Denmark), in case there are at least two languages defined for that specific application. 

> If there is only one language defined in the NStack web console, the application will use that language

On every launch of the mobile app, NStack checks to see if there are new localizations available and it updates the localization file in the app's bundle. In the case of no Internet connection, the Localization Manager will use the default language specified in NStack (this default language localization is shipped with app, it exists since NStack was added in the development process).


---
currentMenu: ios-Localization
---

## Localization on iOS

To use NStack for translations, you need to install the [NStack translations generator](https://github.com/nodes-ios/nstack-translations-generator). 

After that, all translations will be available through the tr-variable. 

Example: `tr.login.forgotPassword` where `login` is the section and `forgotPassword` is the key from nstack. For example:

~~~~swift
@IBOutlet weak var forgotPasswordButton: UIButton! {
    didSet {
 	forgotPasswordButton.setTitle(tr.login.forgotPassword, for: .normal)
    }
}
~~~~

Read more about **Localization** in the [*Feature/Localization*](../../features/localize.html) section.

## 🔧 Setup

1. In your Xcode project *(build phases)* add **New Run Script Phase** and drag it before **Compile Sources** phase
2. Put in the script below and change your project specific IDs and Paths
3. Everytime you do **Clean** and then **Build**, your translations will be fetched and models generated

**You can find the translations run script [here](https://github.com/nodes-ios/nstack-translations-generator/blob/master/translations_script.sh).**
	

​															or here:


~~~bash
TL_PROJ_ROOT_FOLDER="App"
TL_GEN_PATH="${SRCROOT}/${TL_PROJ_ROOT_FOLDER}/Resources/NStack/nstack-translations-generator.bundle"
TL_CONFIG_PATH="${SRCROOT}/${TL_PROJ_ROOT_FOLDER}/Resources/NStack/NStack.plist"
TL_OUT_PATH="${SRCROOT}/${TL_PROJ_ROOT_FOLDER}/Resources/NStack/Translations"

# Check if doing a clean build
if test -f "${DERIVED_FILE_DIR}/TranslationsGenerator.lock"; then
echo "Not clean build, won't fetch translations this time."
else
echo "Clean build. Getting translations..."
"${TL_GEN_PATH}/Contents/MacOS/nstack-translations-generator" -plist "${TL_CONFIG_PATH}" -output "${TL_OUT_PATH}" -standalone
touch "${DERIVED_FILE_DIR}/TranslationsGenerator.lock" # create lock file
fi
~~~

The Translation Manager picks the language translation based on the phone's selected language and region, e.g. en-DK (where the phone is in English, but the region is Denmark), in case there are at least two languages defined for that specific application. 

> If there is only one language defined in the NStack web console, the application will use that language

On every launch of the mobile app, NStack checks to see if there are new translations available and it updates the translation file in the app's bundle. In the case of no Internet connection, the Translation Manager will use the default language specified in NStack (this default language translation is shipped with app, it exists since NStack was added in the development process).


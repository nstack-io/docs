## Localization on iOS
To use nstack for translations, you need to install the [nstack translations generator](https://github.com/nodes-ios/nstack-translations-generator). 

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
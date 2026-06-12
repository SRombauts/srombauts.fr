---
title: "Adding a “What’s New” screen to your Android application"
date: 2011-04-21 00:11:04 +0200
tags:
  - android
---

In some case, you want users of your application to explicitly approve a License before being able to use your software. Adding an EULA (*End User License Agreement*) screen (a *Dialog*) to pop at the first start of an Android Java Application, is really simple and well documented on the web.

If you want to enforce the EULA at each new release of your application (which could become quickly annoying, beware!), give a [look at this linked blog post a “SimpleEula” sample code showing how to do that simply](http://blog.donnfelker.com/2011/02/17/android-a-simple-eula-for-your-android-apps/). Something like this is needed as well if you want to update the term of the license.

But what I want is a simple “What’s New” screen to show at each new release, but without the EULA annoyance and without”cancel button”. The kind of dialog we are seeing  more and more nowadays in application of the market. From the above linked example, I’ve made a really simple ”What’s New” dialog, here is the **WhatsNewScreen.java** sample code:

```java
public class WhatsNewScreen {
    private static final String LOG_TAG                 = "WhatsNewScreen";

    private static final String LAST_VERSION_CODE_KEY   = "last_version_code";

    private Activity            mActivity;

    // Constructor memorize the calling Activity ("context")
    public WhatsNewScreen(Activity context) {
        mActivity = context;
    }

    // Show the dialog only if not already shown for this version of the application
    public void show() {
        try {
            // Get the versionCode of the Package, which must be different (incremented) in each release on the market in the AndroidManifest.xml
            final PackageInfo packageInfo = mActivity.getPackageManager().getPackageInfo(mActivity.getPackageName(), PackageManager.GET_ACTIVITIES);

            final SharedPreferences prefs = PreferenceManager.getDefaultSharedPreferences(mActivity);
            final long lastVersionCode = prefs.getLong(LAST_VERSION_CODE_KEY, 0);

            if (packageInfo.versionCode != lastVersionCode) {
                Log.i(LOG_TAG, "versionCode " + packageInfo.versionCode + "is different from the last known version " + lastVersionCode);

                final String title = mActivity.getString(R.string.app_name) + " v" + packageInfo.versionName;

                final String message = mActivity.getString(R.string.whatsnew);

                // Show the News since last version
                AlertDialog.Builder builder = new AlertDialog.Builder(mActivity)
                        .setTitle(title)
                        .setMessage(message)
                        .setPositiveButton(android.R.string.ok, new Dialog.OnClickListener() {

                            public void onClick(DialogInterface dialogInterface, int i) {
                                // Mark this version as read
                                SharedPreferences.Editor editor = prefs.edit();
                                editor.putLong(LAST_VERSION_CODE_KEY, packageInfo.versionCode);
                                editor.commit();
                                dialogInterface.dismiss();
                            }
                        });
                builder.create().show();
            } else {
                Log.i(LOG_TAG, "versionCode " + packageInfo.versionCode + "is already known");
            }

        } catch (PackageManager.NameNotFoundException e) {
            e.printStackTrace();
        }
    }

}
```

You have to call it on the **onCreate** of the first activity of your application:

```java
    /** Called when the activity is first created. */
    @Override
    protected void onCreate (Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // Layout of the main activity
        setContentView(R.layout.main);

        // Show the "What's New" screen once for each new release of the application
        new WhatsNewScreen(this).show();

        ...
    }
```

Here is an example of the XML string resource used **res/values/strings.xml**:

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    ...

    <string name="whatsnew">
        - Removed many SQLite exception stack\n
        - Improved the way the application launch on notification (no more multi-activity stacking)\n
        - Added this What\'s new screen\n
    </string>

    ...
</resources>
```

Enjoy!

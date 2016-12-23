#material-about-library
--------

Makes it easy to create a beautiful about screen for your app.

Idea from here: https://github.com/HeinrichReimer/open-source-library-request-manager/issues/3

Design inspired by Phonograph.


Features
--------

* Material design
* Modular backend
* Easy to implement
* Fluent API

Setup
-----

**Step 1:** Your `Activity` must extend `MaterialAboutActivity` and be in your *AndroidManifest.java*:
```java
public class ExampleMaterialAboutActivity extends MaterialAboutActivity {

    @Override
    protected MaterialAboutList getMaterialAboutList() {
        return new MaterialAboutList.Builder()
                .build();
    }

}
```

```xml
<manifest ...>
    <application ...>
        <activity android:name=".ExampleMaterialAboutActivity"
            android:theme="@style/AppTheme.MaterialAboutActivity"/>
    </application>
</manifest>
```

```xml
    <style name="AppTheme.MaterialAboutActivity" parent="Theme.Mal" >
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>
```

**Step 2:** Add Cards:
```java
public class ExampleMaterialAboutActivity extends MaterialAboutActivity {

    @Override
    protected MaterialAboutList getMaterialAboutList() {

        MaterialAboutCard.Builder appCardBuilder = new MaterialAboutCard.Builder();
        
        // Add items to card
        
        appCardBuilder.addItem(new MaterialAboutTitleItem.Builder()
                .text("Material About Library")
                .icon(R.mipmap.ic_launcher)
                .build());
        appCardBuilder.addItem(new MaterialAboutActionItem.Builder()
                .text("Version")
                .subText("1.0.0")
                .icon(R.drawable.ic_about_info)
                .setOnClickListener(new MaterialAboutActionItem.OnClickListener() {
                    @Override
                    public void onClick() {
                        Log.i("test", "onClick: Version Tapped");
                        Toast.makeText(ExampleMaterialAboutActivity.this, "Version Tapped", Toast.LENGTH_SHORT).show();
                    }
                })
                .build());
        appCardBuilder.addItem(new MaterialAboutActionItem.Builder()
                .text("Changelog")
                .icon(R.drawable.ic_about_changelog)
                .setOnClickListener(new MaterialAboutActionItem.OnClickListener() {
                    @Override
                    public void onClick() {
                        Toast.makeText(ExampleMaterialAboutActivity.this, "Changelog Tapped", Toast.LENGTH_SHORT).show();
                    }
                })
                .build());
        appCardBuilder.addItem(new MaterialAboutActionItem.Builder()
                .text("Licenses")
                .icon(R.drawable.ic_about_licenses)
                .setOnClickListener(new MaterialAboutActionItem.OnClickListener() {
                    @Override
                    public void onClick() {
                        Toast.makeText(ExampleMaterialAboutActivity.this, "Licenses Tapped", Toast.LENGTH_SHORT).show();
                    }
                })
                .build());

        MaterialAboutCard.Builder authorCardBuilder = new MaterialAboutCard.Builder();
        authorCardBuilder.title("Author");

        authorCardBuilder.addItem(new MaterialAboutActionItem.Builder()
                .text("Daniel Stone")
                .subText("United Kingdom")
                .icon(R.drawable.ic_about_person)
                .build());

        authorCardBuilder.addItem(new MaterialAboutActionItem.Builder()
                .text("Fork on GitHub")
                .icon(R.drawable.ic_about_github)
                .setOnClickListener(new MaterialAboutActionItem.OnClickListener() {
                    @Override
                    public void onClick() {
                        Intent i = new Intent(Intent.ACTION_VIEW);
                        i.setData(Uri.parse("https://github.com/daniel-stoneuk"));
                        startActivity(i);
                    }
                })
                .build());

        MaterialAboutCard.Builder supportCardBuilder = new MaterialAboutCard.Builder();
        supportCardBuilder.title("Support Development");
        supportCardBuilder.addItem(new MaterialAboutActionItem.Builder()
                .text("Report Bugs")
                .subText("Report bugs or request new features.")
                .icon(R.drawable.ic_about_bug)
                .setOnClickListener(new MaterialAboutActionItem.OnClickListener() {
                    @Override
                    public void onClick() {
                        Toast.makeText(ExampleMaterialAboutActivity.this, "Bug report tapped", Toast.LENGTH_SHORT).show();
                    }
                })
                .build());

        return new MaterialAboutList.Builder()
                .addCard(appCardBuilder.build())
                .addCard(authorCardBuilder.build())
                .addCard(supportCardBuilder.build())
                .build();
    }

}
```
Item types:

- `MaterialAboutActionItem`: Standard item with text, icon and optional subtext.
- `MaterialAboutTitleItem`: Larger item with large icon (eg app icon) and larger text.

License
-------

    Copyright 2016 Daniel Stone

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
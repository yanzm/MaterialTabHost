MaterialTabHost
===============

TabHost along with the specifications of the Material design
http://www.google.com/design/spec/components/tabs.html

Usage
---------------

### build.gradle

```
repositories {
    maven { url 'http://yanzm.github.io/MaterialTabHost/repository' }
}

dependencies {
    compile 'net.yanzm:mth:1.0.1'
}
```

### Layout XML

```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".SampleActivity">

    <net.yanzm.mth.MaterialTabHost
        android:id="@android:id/tabhost"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

    <android.support.v4.view.ViewPager
        android:id="@+id/pager"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</LinearLayout>
```

### Set up

```
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_sample);

        if (getSupportActionBar() != null) {
            getSupportActionBar().setElevation(0);
        }

        MaterialTabHost tabHost = (MaterialTabHost) findViewById(android.R.id.tabhost);
        tabHost.setType(MaterialTabHost.Type.FullScreenWidth);
//        tabHost.setType(MaterialTabHost.Type.Centered);
//        tabHost.setType(MaterialTabHost.Type.LeftOffset);

        SectionsPagerAdapter pagerAdapter = new SectionsPagerAdapter(getSupportFragmentManager());
        for (int i = 0; i < pagerAdapter.getCount(); i++) {
            tabHost.addTab(pagerAdapter.getPageTitle(i));
        }

        final ViewPager viewPager = (ViewPager) findViewById(R.id.pager);
        viewPager.setAdapter(pagerAdapter);
        viewPager.setOnPageChangeListener(tabHost);

        tabHost.setOnTabChangeListener(new MaterialTabHost.OnTabChangeListener() {
            @Override
            public void onTabSelected(int position) {
                viewPager.setCurrentItem(position);
            }
        });
    }
```

### Color

#### Default

* backbround color : colorPrimary
* indicator color : colorAccent or colorControlActivated

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
        <item name="colorPrimaryDark">#00695C</item>
        <item name="colorPrimary">#00897B</item>
        <item name="colorAccent">#FFD54F</item>
    </style>
</resources>
```

#### attributes

* indicator color : colorTabIndicator

```
    <net.yanzm.mth.MaterialTabHost
        android:id="@android:id/tabhost"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:colorTabIndicator="#ff0000" />

```


### Type

#### MaterialTabHost.Type.FullScreenWidth

![FullScreenWidth](http://3.bp.blogspot.com/-4szD4lkQH74/VIfGci0GOkI/AAAAAAAARUQ/xObIpgmHhKI/s400/mth_fullwidth.png)

#### MaterialTabHost.Type.Centered

![LeftOffset](http://2.bp.blogspot.com/-UAIRu67QxE0/VIfGcncmBfI/AAAAAAAARUM/-kXX7OS9oeI/s400/mth_centered.png)

#### MaterialTabHost.Type.LeftOffset

![LeftOffset](http://2.bp.blogspot.com/-C9_JSDk9D1Y/VIfGcx9dcfI/AAAAAAAARUU/xwgTMuW2YCs/s400/mth_leftoffset.png)



LICENSE
---------------

```
Copyright 2014 Yuki Anzai

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

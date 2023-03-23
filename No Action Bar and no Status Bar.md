# Change from XML
## Add this lines to themes.xml in the AppTheme style
```XML
<item name="windowActionBar">false</item>
<item name="windowNoTitle">true</item>
<item name="android:fitsSystemWindows">true</item>
<item name="android:windowTranslucentStatus">true</item>
<item name="android:windowTranslucentNavigation">true</item>
```
# Change from Kotlin code
## Add this lines to MainActivity.kt in onCreate
```kotlin
window.apply {
	clearFlags(WindowManager.LayoutParams.FLAG_TRANSLUCENT_STATUS)
	addFlags(WindowManager.LayoutParams.FLAG_DRAWS_SYSTEM_BAR_BACKGROUNDS)
	when (context.resources?.configuration?.uiMode?.and(Configuration.UI_MODE_NIGHT_MASK)) {
		Configuration.UI_MODE_NIGHT_YES -> decorView.systemUiVisibility =
			View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
		else -> decorView.systemUiVisibility =
			View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN or View.SYSTEM_UI_FLAG_LIGHT_STATUS_BAR
	}
	statusBarColor = Color.TRANSPARENT
}
```        
## Add this line to themes.xml in the AppTheme style
```XML
<item name="android:fitsSystemWindows">true</item>
```

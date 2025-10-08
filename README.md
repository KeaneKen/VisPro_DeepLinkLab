### Deep Link Definition
A deep link is a URL that takes users directly to a specific screen or piece of content inside a mobile app, rather than just launching the app’s home screen.

For example, myapp://product/123 can open the app and navigate straight to the product with ID 123.

Why it’s used:

- Improved user experience: Lets users jump directly to relevant content.
- Marketing and sharing: Enables links from ads, emails, or websites to open the correct app screen.
- Re-engagement: Encourages users to return to the app through personalized or contextual links.
- Cross-platform consistency: Allows the same link to work across web and mobile environments.

### Concept Check

**1. Route vs Deep Link**
A route is a in app navigation path managed by Flutter's Framework.
Meanwhile deep link is a system level URL that when the link is clicked, it launches the app and passes the data to flutter.

**2. Intent Filter**
Android needs an intent filter so that the OS knows which app can run the URL.

---

### Technical Understanding

**3. Role of uni_links Package**
The uni_links package bridges Android/iOS deep links and Flutter's navigation. It detects when a link is opened and passes the link to Darts so it can be navigated

**4. When Deep Link Opens While App Is Running**
If the app is already running, `uni_links` emits the new link through its stream (`linkStream`), allowing the app to respond dynamically—typically by navigating to the target page without restarting the app.

---

### Debugging Insight

**5. adb Opens App but Doesn’t Navigate**
First, check your AndroidManifest.xml `intent-filter` section—especially the `<data>` tag’s `scheme`, `host`, and `pathPrefix`. If these don’t match your test link, Android will open the app but not deliver the deep link to Flutter.
Next, verify your `uni_links` listener logic in Dart to ensure it handles the incoming URI properly.

### Wrap-Up Sumary
- Deep linking connects Flutter’s internal navigation system with Android’s intent filters, allowing URLs or app links to trigger navigation to specific Flutter routes.
- It's useful when user is clicking a link to your app, deep link is making the link able to open the app immediately
- Using adb is honestly pretty infuriating at first, but the way to solve it is just to add a path in the environment variable for it, and of course, the uni_links, i've solved it by changing it to a newer version, app_links

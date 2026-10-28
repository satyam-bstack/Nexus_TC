# 🚀 Hands-on Workshop: Getting Started with BrowserStack Test Companion for Mobile App Testing

**Audience:** SOK Group Engineering & QA Teams  
**Level:** Introductory / Hands-on Sandbox  
**App under Test:** [Nexus Demo iOS App (v1.0.0 IPA)](https://github.com/BrowserStackCE/browserstack-demo-hub/releases/download/1.0.0/nexus-demo.ipa)  
**Confluence Guide:** [Nexus App for Custom Demo](https://browserstack.atlassian.net/wiki/spaces/CE/pages/6618218667/Nexus+App+for+Custom+Demo)  

---

## 🎯 What You'll Learn Today

By the end of this session, you will be able to:
1. **Set up** Test Companion in your IDE in under 5 minutes.
2. **Generate** mobile automation tests (Appium / WebdriverIO / Python / Java) from plain English prompts and UI screenshots.
3. **Execute** tests on real iOS and Android devices in the BrowserStack cloud.
4. **Fix failing tests** automatically using AI root-cause analysis ("Fix Test").
5. **Explore freely:** experiment with real-world scenarios like biometrics, camera scanning, and geolocation across dedicated hands-on labs.

---

## ⏱️ Quick Agenda (2 – 2.5 Hours)

* **00:00 – 00:20 | Quick Start & Setup:** Install plugin, login, and clone the starter project.
* **00:20 – 00:50 | Lab 1 & Lab 2:** Prompt Test Companion to generate your first test and execute it on cloud real devices.
* **00:50 – 01:20 | Lab 3 & Lab 4:** Intentional failure and AI self-healing ("Fix Test"), plus multimodal test generation from UI screenshots.
* **01:20 – 02:00 | Lab 5: Sandbox Challenges (Pick Your Own Adventure):** Choose retail, banking (biometrics), or travel (geolocation).
* **02:00 – 02:15 | Show & Tell + Q&A:** Share learnings, prompt patterns, and next steps for team rollout.

---

## 🧰 Step 0: 5-Minute Setup

### 1. Install the IDE Plugin
* Open **VS Code** (or JetBrains IntelliJ / Android Studio).
* Search for **BrowserStack Test Companion** in the Extensions / Plugins marketplace and click **Install**.

### 2. Sign In to BrowserStack
* Open the Test Companion icon on the sidebar.
* Click **Sign In** and authenticate with your BrowserStack credentials.

### 3. Get the App & Starter Code
* **Sample App:** Download [nexus-demo.ipa](https://github.com/BrowserStackCE/browserstack-demo-hub/releases/download/1.0.0/nexus-demo.ipa) (or the Android APK if testing on Android).
* **Starter Repo:** Clone the hands-on repo:
  ```bash
  git clone https://github.com/BrowserStackCE/app_automate_e2eflow.git
  cd app_automate_e2eflow
  npm install   # or your framework's package install
  ```

---

## 🧪 Hands-On Labs

---

### 🟢 Lab 1: Generate Your First Test in Plain English
**Objective:** Experience how Test Companion turns natural language into a working, framework-native Appium test script.

#### Instructions:
1. Open the **Test Companion** chat panel in your IDE.
2. Select the **E-Commerce / Retail Flow** in the Nexus app (representing everyday *S-Kaupat / Prisma* retail scenarios).
3. Paste the following prompt into Test Companion:
   > *"Write an Appium test for the Nexus demo app that launches the app, switches to the E-Commerce domain, searches for 'Organic Apples', adds 2 items to the cart, and asserts that the cart badge shows 2."*
4. Review the generated code in the diff viewer.
5. Click **Insert into File** or save it as `tests/ecommerce-cart.test.js`.

---

### 🟢 Lab 2: Run on a Real Cloud Device (App Automate)
**Objective:** Execute your newly authored test directly against real iOS and Android hardware in the BrowserStack cloud.

#### Instructions:
1. In the Test Companion interface, click **Run on BrowserStack** (or execute via your configured npm/test runner command).
2. Select your target device profile:
   * **iOS:** *Apple iPhone 15 (iOS 17)*
   * **Android:** *Samsung Galaxy S24 (Android 14)*
3. Monitor the live execution stream directly inside your IDE sidebar.
4. Click the generated test session link to open the BrowserStack Dashboard and inspect:
   * **Video Recording** of the physical device run.
   * **Device Console & Appium Logs**.
   * **Network Activity & Step-by-Step Screenshots**.

---

### 🟡 Lab 3: Break the Test & Let AI Heal It ("Fix Test")
**Objective:** Experience zero-touch AI maintenance and root-cause analysis when UI locators change or break.

#### Instructions:
1. Open your test file (`tests/ecommerce-cart.test.js`) and intentionally break an element selector:
   * Example: change `id="btn_add_to_cart"` to `id="btn_add_to_bag_wrong"`.
2. Re-run the test suite on App Automate — observe the test fail with an `ElementNotFoundError`.
3. In Test Companion's results panel, locate the failed step and click **Fix Test**.
4. Review the AI's diagnostic analysis:
   * It inspects the failure stack trace alongside the runtime device screenshot.
   * It identifies the intended element and suggests the correct, updated selector.
   * It presents a clean Git diff.
5. Click **Apply Changes** and re-run the test to verify it passes! 🎉

---

### 🟡 Lab 4: Generate Tests from a Screenshot or UI Mockup
**Objective:** Leverage multimodal AI to author full test assertions directly from visual assets without manually inspecting DOM/accessibility trees.

#### Instructions:
1. Capture a screenshot of any screen in the Nexus demo app (or grab one from the [Confluence Guide](https://browserstack.atlassian.net/wiki/spaces/CE/pages/6618218667/Nexus+App+for+Custom+Demo)).
2. Drag and drop the screenshot directly into the Test Companion chat window.
3. Prompt Test Companion:
   > *"Look at this screen. Write test assertions to verify that all primary call-to-action buttons, prices, and header text elements are displayed correctly."*
4. Review the generated test assertions, append them to your test suite, and run the validation.

---

### 🔵 Lab 5: Sandbox Challenges (Pick Your Own Adventure)
**Objective:** Apply your skills to advanced mobile testing use cases mirroring SOK Group’s customer services. Pick at least one challenge below:

#### Challenge 5A: S-Pankki Scenario — Biometric Authentication (FaceID / TouchID)
* **Context:** Secure financial transactions and login authentication.
* **Task:** Use the Nexus Banking flow and prompt Test Companion:
  > *"Create an Appium test for the Nexus Banking login flow using BrowserStack's biometric injection capability. Simulate a successful FaceID login, and then simulate a failed FaceID attempt to verify the fallback PIN prompt appears."*

#### Challenge 5B: Sokos Hotels Scenario — Geolocation & Network Simulation
* **Context:** Location-aware hotel booking, local discovery, and on-the-go connectivity handling.
* **Task:** Prompt Test Companion:
  > *"Write a test that sets the device GPS location to Helsinki coordinates (60.1699° N, 24.9384° E), searches for nearby hotels in the Travel section, and verifies that the app handles simulated 3G network throttling gracefully."*

#### Challenge 5C: Camera & Barcode Scanning (Image Injection)
* **Context:** In-store scanning, receipt capture, and QR loyalty card verification.
* **Task:** Prompt Test Companion:
  > *"Generate a test that uses BrowserStack Image Injection to pass a sample QR code image to the Nexus app camera scanner and verifies the scan result."*

---

## 💡 Prompting Tips for Test Companion

* **Be explicit about the framework:** e.g., *"using WebdriverIO with Mocha"* or *"using Appium Java with JUnit 5"*.
* **Specify assertions:** Tell the AI what success looks like (e.g., *"assert that the confirmation toast message contains 'Booking Confirmed'"*).
* **Ask for Page Objects:** If you prefer clean architecture, say: *"Generate this test using the Page Object Model pattern"*.

---

## 🙋 Help & Facilitators
* **Need help during the workshop?** Drop a message in the workshop Slack/Teams channel or raise your hand.
* **Useful Links:**
  * [BrowserStack App Automate Docs](<redacted URL>)
  * [Nexus App Confluence Page](https://browserstack.atlassian.net/wiki/spaces/CE/pages/6618218667/Nexus+App+for+Custom+Demo)

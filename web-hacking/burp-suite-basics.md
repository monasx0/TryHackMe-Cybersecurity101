# Burp Suite Basics

## Task 1 - Introduction

This module aims to help you understand the basics of the **Burp Suite** web application security testing framework. Our focus includes:

- A thorough introduction to **Burp Suite**
- A comprehensive overview of various tools available within the framework
- Detailed guidance on installing **Burp Suite** on your system
- Navigating and configuring **Burp Suite**

---

## Task 2 - What is Burp Suite

**Burp Suite** is a **Java-based framework** designed as a comprehensive solution for conducting **web application penetration testing**. It has become the industry standard tool for hands-on security assessments of web and mobile applications, including those that rely on **application programming interfaces (APIs)**.

Simply put, **Burp Suite** captures and enables manipulation of all **HTTP/HTTPS traffic** between a **browser** and a **web server**. This fundamental capability forms the backbone of the framework. By **intercepting requests**, users can route them to various components within **Burp Suite**. The ability to **intercept**, view, and modify **web requests** before they reach the target server, or manipulate **responses** before they reach our browser, makes **Burp Suite** invaluable for manual **web application testing**.

---

### Burp Suite Editions

**Burp Suite** is available in different editions:

#### Burp Suite Community Edition
- Freely accessible for non-commercial use within legal boundaries
- Focus of this room

#### Burp Suite Professional
An unrestricted version with advanced features:
- **Automated vulnerability scanner**
- **Fuzzer/brute-forcer** that isn't rate limited
- Saving projects for future use and **report generation**
- Built-in **API** for integration with other tools
- Unrestricted access to add new **extensions**
- Access to the **Burp Suite Collaborator** (unique request catcher)

**Burp Suite Professional** is a highly potent tool, making it the preferred choice for professionals.

#### Burp Suite Enterprise
- Primarily used for **continuous scanning**
- Features an **automated scanner** that periodically scans web applications for vulnerabilities
- Resides on a **server** and constantly scans target web applications
- Unlike other editions that allow manual attacks from a local machine

Due to requiring a license for **Professional** and **Enterprise** editions, we will focus on the core feature set provided by **Burp Suite Community Edition**.

---

## Task 3 - Features of Burp Community

Although **Burp Suite Community** offers a more limited feature set compared to the **Professional edition**, it still provides valuable tools for **web application testing**:

### Proxy
The **Burp Proxy** is the most renowned aspect of **Burp Suite**. It enables **interception** and modification of **requests** and **responses** while interacting with web applications.

### Repeater
**Repeater** allows for capturing, modifying, and resending the same **request** multiple times. This is particularly useful when crafting **payloads** through trial and error (e.g., in **SQLi - SQL Injection**) or testing endpoint functionality for vulnerabilities.

### Intruder
Despite rate limitations in **Burp Suite Community**, **Intruder** allows for spraying **endpoints** with requests. It is commonly used for **brute-force attacks** or **fuzzing endpoints**.

### Decoder
**Decoder** offers a valuable service for data transformation. It can decode captured information or encode **payloads** before sending them to the target. Leveraging **Decoder** within **Burp Suite** is highly efficient.

### Comparer
**Comparer** enables comparison of two pieces of data at either the word or byte level. The ability to send large data segments directly to a comparison tool with a single keyboard shortcut significantly accelerates the process.

### Sequencer
**Sequencer** is typically employed when assessing the randomness of **tokens**, such as **session cookie values** or other supposedly randomly generated data. If the algorithm lacks secure randomness, it can expose avenues for devastating attacks.

---

#### Extensions

The **Java codebase** of **Burp Suite** facilitates development of **extensions** to enhance functionality. These **extensions** can be written in:
- **Java**
- **Python** (using the Java Jython interpreter)
- **Ruby** (using the Java JRuby interpreter)

The **Burp Suite Extender** module allows quick and easy loading of **extensions** into the framework. The marketplace, known as the **BApp Store**, enables downloading third-party modules. While certain **extensions** require a professional license, many are available for **Burp Community**. For example, the **Logger++** module can extend the built-in logging functionality.

---

## Task 4 - Installation

**Burp Suite** is useful for **web** or **mobile application assessments**, **pentesting**, **bug bounty hunting**, or debugging features in web app development.

### Download Options

**Kali Linux**: **Burp Suite** comes pre-installed. If missing, install it from the Kali apt repositories.

**Linux, macOS, and Windows**: PortSwigger provides dedicated installers for **Burp Suite Community** and **Professional** on the Burp Suite downloads page. Choose your operating system and select **Burp Suite Community Edition**, then click Download.

### Installation Steps

Install **Burp Suite** using the appropriate method for your operating system:
- **Windows**: Run the executable file
- **Linux**: Execute the script from the terminal (with or without sudo)

If you choose not to use sudo during installation on Linux, **Burp Suite** will be installed in your home directory at `~/BurpSuiteCommunity/BurpSuiteCommunity` and will not be added to your PATH.

The installation wizard provides clear instructions. It's generally safe to accept default settings, but always review the installer carefully.

---

## Task 5 - The Dashboard

Launch **Burp Suite** and accept the terms and conditions. You'll be prompted to select a **project type**. In **Burp Suite Community**, simply click **Next**.

The next window allows you to choose the configuration. It's generally recommended to keep the default settings. Click **Start Burp** to open the main interface.

### Dashboard Quadrants

The **Burp Dashboard** is divided into four quadrants (counter-clockwise from top left):

#### 1. Tasks
The **Tasks** menu allows you to define background tasks that **Burp Suite** performs while you use the application. The default "**Live Passive Crawl**" task automatically logs pages visited. **Burp Suite Professional** offers additional features like on-demand scans.

#### 2. Event Log
The **Event log** provides information about actions performed by **Burp Suite**, such as starting the **proxy** and details about connections made through Burp.

#### 3. Issue Activity
This section is specific to **Burp Suite Professional**. It displays **vulnerabilities** identified by the **automated scanner**, ranked by severity and filterable based on certainty.

#### 4. Advisory
The **Advisory** section provides detailed information about identified **vulnerabilities**, including references and suggested remediations. This information can be exported into a report. In **Burp Suite Community**, this section may not show any vulnerabilities.

### Help Icons

Throughout various tabs and windows, you'll notice **question mark icons**. Clicking these opens a new window with helpful information specific to that section. These help icons are invaluable when you need assistance.

---

## Task 6 - Navigation

**Burp Suite** navigation is primarily done through the top menu bars, which allow switching between modules and accessing sub-tabs.

### Navigation Methods

**Module Selection**: The top row displays available modules. Click on each module to switch between them.

**Sub-Tabs**: If a selected module has multiple sub-tabs, access them through the second menu bar directly below the main menu bar. These sub-tabs contain module-specific settings and options.

**Detaching Tabs**: To view multiple tabs separately, go to the **Window** option in the application menu. Choose the "**Detach**" option, and the selected tab will open in a separate window. Detached tabs can be reattached using the same method.

### Keyboard Shortcuts

| Shortcut | Tab |
|----------|-----|
| `Ctrl + Shift + D` | Dashboard |
| `Ctrl + Shift + T` | Target tab |
| `Ctrl + Shift + P` | Proxy tab |
| `Ctrl + Shift + I` | Intruder tab |
| `Ctrl + Shift + R` | Repeater tab |

---

## Task 7 - Options

Before diving into the **Burp Proxy**, let's explore available options for configuring **Burp Suite**. There are two types of settings:

### Global Settings (User Settings)
These settings affect the entire **Burp Suite** installation and are applied every time you start the application. They provide a baseline configuration.

### Project Settings
These settings are specific to the current project and apply only during the session. **Burp Suite Community Edition** does not support saving projects, so project-specific options will be lost when you close Burp.

### Accessing Settings

Click on the **Settings** button in the top navigation bar to open a separate settings window.

### Settings Window Menu

The Settings window includes a menu on the left-hand side with:
- **Search**: Search for specific settings using keywords
- **Type filter**: Filter settings for User and Project options
- **User settings**: Settings affecting the entire installation
- **Project settings**: Settings specific to the current project
- **Categories**: Select settings by category

Many tools within **Burp Suite** provide shortcuts to specific categories of settings. For example, the **Proxy** module includes a **Proxy settings** button that opens the settings window directly to the relevant proxy section.

The **search feature** is valuable, allowing you to quickly search for settings using keywords.

---

## Task 8 - Introduction to the Burp Proxy

The **Burp Proxy** is a fundamental and crucial tool within **Burp Suite**. It enables capture of **requests** and **responses** between the user and the target **web server**. This **intercepted traffic** can be manipulated, sent to other tools, or allowed to continue to its destination.

### Key Points About Burp Proxy

#### Intercepting Requests
When **requests** are made through the **Burp Proxy**, they are intercepted and held back from reaching the target server. The **requests** appear in the **Proxy** tab, allowing actions such as forwarding, dropping, editing, or sending them to other Burp modules. To disable the intercept and allow **requests** to pass through without interruption, click the **Intercept is on** button.

#### Taking Control
The ability to **intercept requests** empowers testers to gain complete control over web traffic, making it invaluable for testing web applications.

#### Capture and Logging
**Burp Suite** captures and logs **requests** made through the **proxy** by default, even when interception is turned off. This logging functionality helps with later analysis and review.

#### WebSocket Support
**Burp Suite** also captures and logs **WebSocket communication**, providing additional assistance when analyzing web applications.

#### Logs and History
Captured **requests** can be viewed in the **HTTP history** and **WebSockets history** sub-tabs, allowing for retrospective analysis and sending **requests** to other Burp modules.

### Proxy Settings

**Proxy-specific options** can be accessed by clicking the **Proxy settings** button.

#### Notable Features

**Response Interception**: By default, the **proxy** does not intercept server **responses** unless explicitly requested. The "**Intercept responses based on the following rules**" checkbox allows for flexible response interception.

**Match and Replace**: This section enables use of **regular expressions (regex)** to modify incoming and outgoing **requests**. This feature allows dynamic changes, such as modifying the **user agent** or manipulating **cookies**.

---

## Task 9 - Connecting through the Proxy (FoxyProxy)

To use the **Burp Suite Proxy**, we need to configure our local web browser to redirect traffic through **Burp Suite**. We'll focus on configuring the **proxy** using the **FoxyProxy extension** in Firefox.

### Configuration Steps

#### 1. Install FoxyProxy
Download and install the **FoxyProxy Basic extension**.

**Note**: FoxyProxy is already installed on the AttackBox.

#### 2. Access FoxyProxy Options
Once installed, a button will appear at the top right of the Firefox browser. Click the **FoxyProxy** button to access the options pop-up.

#### 3. Create Burp Proxy Configuration
In the **FoxyProxy** options pop-up, click the **Options** button. This opens a new browser tab with configurations. Click **Add** to create a new **proxy** configuration.

#### 4. Add Proxy Details
On the "Add Proxy" page, fill in:
- **Title**: Burp (or any preferred name)
- **Proxy IP**: `127.0.0.1`
- **Port**: `8080`

#### 5. Save Configuration
Click **Save** to save the **Burp Proxy** configuration.

#### 6. Activate Proxy Configuration
Click on the **FoxyProxy** icon at the top-right of Firefox and select the Burp configuration. This redirects browser traffic through `127.0.0.1:8080`. **Burp Suite** must be running for your browser to make requests.

#### 7. Enable Proxy Intercept
Switch to **Burp Suite** and ensure **Intercept** is turned on in the **Proxy** tab.

#### 8. Test the Proxy
Open Firefox and try accessing a website. Your browser will hang, and the **proxy** will populate with the **HTTP request**. Congratulations, you've intercepted your first request!

### Important Notes

- When the **proxy** configuration is active and **intercept** is switched on, your browser will hang whenever you make a **request**
- Be cautious not to leave **intercept** switched on unintentionally
- Right-clicking on a **request** in **Burp Suite** allows various actions: forwarding, dropping, sending to other tools, or selecting options

**Note**: Consider closing other tabs in the AttackBox browser before enabling interception to avoid receiving **WebSocket requests** instead of requests from the target VM.

---

## Task 10 - Site Map and Issue Definitions

The **Target** tab in **Burp Suite** provides more than just scope control. It consists of three sub-tabs:

### Site Map
This sub-tab allows mapping out web applications in a tree structure. Every page visited while the **proxy** is active will be displayed on the **site map**. This enables automatic site map generation by simply browsing the web application. In **Burp Suite Professional**, you can use the **site map** to perform automated crawling, exploring links between pages. Even with **Burp Suite Community**, you can utilize the **site map** to accumulate data during initial enumeration steps. It's particularly useful for mapping out **APIs**, as any **API endpoints** accessed will be captured.

### Issue Definitions
Although **Burp Community** doesn't include full **vulnerability scanning** functionality, we still have access to a list of all **vulnerabilities** the scanner looks for. The **Issue definitions** section provides an extensive list of web vulnerabilities with descriptions and references. This resource is valuable for referencing **vulnerabilities** in reports or describing a particular **vulnerability** identified during manual testing.

### Scope Settings
This setting allows controlling the target scope in **Burp Suite**. It enables including or excluding specific domains/IPs to define the scope of testing. By managing the scope, you can focus on specific web applications and avoid capturing unnecessary traffic.

---

## Task 11 - The Burp Suite Browser

In addition to modifying our regular web browser to work with the **proxy**, **Burp Suite** includes a built-in **Chromium browser** that is pre-configured to use the **proxy** without modifications.

### Starting the Burp Browser

To start the **Burp Browser**, click the **Open Browser** button in the **proxy** tab. A Chromium window will pop up, and any **requests** made in this browser will go through the **proxy**.

**Note**: There are many settings related to the **Burp Browser** in project options and user options settings. Explore and customize them as needed.

### Linux Root User Issue

If running **Burp Suite** on Linux as the root user (as with the AttackBox), you may encounter an error preventing the **Burp Browser** from starting due to inability to create a sandbox environment.

#### Solutions

**Smart option**: Create a new user and run **Burp Suite** under a low-privilege account.

**Easy option**: Go to **Settings → Tools → Burp's browser** and check the "**Allow Burp's browser to run without a sandbox**" option. This allows the browser to start without a sandbox. However, this option is disabled by default for security reasons. If enabled, exercise caution, as compromising the browser could grant an attacker access to your entire machine.

---

## Task 12 - Scoping and Targeting

One of the most important aspects of using the **Burp Proxy** is **scoping**.

### Why Scoping Matters

Capturing and logging all traffic can quickly become overwhelming. **Scoping** allows us to define what gets proxied and logged in **Burp Suite**. We can restrict **Burp Suite** to target only specific web applications we want to test.

### Setting Up Scope

The easiest way to set up scope is by:
1. Switch to the **Target** tab
2. Right-click on your target from the list on the left
3. Select **Add To Scope**
4. **Burp** will prompt whether to stop logging anything not in scope (select **yes** in most cases)

### Checking Scope

To check your scope, switch to the **Scope settings** sub-tab within the **Target** tab. The **Scope settings** window allows controlling target scope by including or excluding domains/IPs.

### Preventing Out-of-Scope Interception

Even if we disabled logging for out-of-scope traffic, the **proxy** will still intercept everything. To prevent this:
1. Go to the **Proxy settings** sub-tab
2. Select "**And URL Is in target scope**" from the "**Intercept Client Requests**" section

Enabling this option ensures the **proxy** completely ignores any traffic not within the defined scope, resulting in cleaner traffic view.

---

## Task 13 - Proxying HTTPS

**Note**: The AttackBox is already configured to solve this problem. If using the AttackBox, you can skip to the next task.

### The Issue

When intercepting **HTTP traffic**, we may encounter an issue when navigating to sites with **TLS enabled**. For example, when accessing `https://google.com/`, we may receive an error indicating that the **PortSwigger Certificate Authority (CA)** is not authorized to secure the connection. This happens because the browser doesn't trust the **certificate** presented by **Burp Suite**.

### Solution Steps

#### 1. Download the CA Certificate
With the **Burp Proxy** activated, navigate to `http://burp/cert`. This will download a file called `cacert.der`. Save this file on your machine.

#### 2. Access Firefox Certificate Settings
Type `about:preferences` into your Firefox URL bar and press Enter. This takes you to the Firefox settings page. Search for "**certificates**" and click the **View Certificates** button.

#### 3. Import the CA Certificate
In the **Certificate Manager** window, click **Import**. Select the `cacert.der` file you downloaded.

#### 4. Set Trust for the CA Certificate
In the subsequent window, check the box "**Trust this CA to identify websites**" and click **OK**.

By completing these steps, we've added the **PortSwigger CA certificate** to our list of trusted **certificate authorities**. Now, we can visit any **TLS-enabled** site without encountering the certificate error.

---

## Task 14 - Conclusion

You now have a solid understanding of the **Burp Suite** interface, configuration options, and the **Burp Proxy**. These skills will be essential as you continue your journey in **web** and **mobile application penetration testing**.



The more you use **Burp Suite**, the more proficient you'll become in identifying and exploiting **vulnerabilities** in web applications.


---

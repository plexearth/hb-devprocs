## **Feature Title:** 

## **Switching Between Editions (CLASSIC to LITE and vice versa)**

**Date:** 2024-07-29  
**Author:** [Lambros Kaliakatsos](mailto:lkaliakatsos@plexscape.com)

---

## **Overview**

**Summary:**  
This feature enables Plex-Earth users to switch between different editions, such as CLASSIC (fully-fledged/paid plans) and LITE (free plan). It addresses the problem of users needing flexibility to continue using Plex-Earth after their free trial or subscription has expired, or to try out the full version if they are currently on the LITE plan.

**Benefits:**

* Allows users to continue using Plex-Earth without interruption by switching to the LITE version after their trial or subscription ends.  
* Provides flexibility for LITE users to experience the full capabilities of the CLASSIC version.  
* Helps users manage costs by allowing them to switch to a free plan when they no longer need premium features.  
* Business-wise, this feature is expected to stimulate conversions of LITE users to paid plans. It allows trial or existing users to access the free version, maintaining their engagement with Plex-Earth, and potentially converting to paid plans or renewing expired subscriptions in the future.

## **Details**

**Functionality:**  
Each Edition is another Application in Wings, the licensing system, and a user starts with Plex-Earth activated on their workstation in one of the Editions (free trial users, subscribers, or Lite version users).

Plex-Earth offers a transition to another Edition under specific circumstances:

* **Free Trial Offer:** A message offers a Lite user a free trial of the Pro version (CLASSIC Edition).  
* **Upgrade Offer:** A message prompts users to upgrade to a paid plan (Pro \- CLASSIC).  
* **Free Trial Expiry:** When the free trial has finished, a message allows users to either upgrade to a paid plan (Pro—CLASSIC) or continue with the free version (LITE Edition).  
* **Subscription Expiry:** When a subscription expires, a message gives users the option to renew it or fall back to the LITE version.

Users can also switch to another edition through the "My Account" section in Plex-Earth.  
In any case, the user will have to click a button to "Accept" and initiate the transition to the other Edition.

**Usage:**

1. When Plex-Earth prompts users with a message offering a switch (e.g., free trial offer, subscription expiration notice), users can follow the on-screen instructions to switch editions.  
1. Alternatively, users can manually navigate to "My Account" in Plex-Earth, select the option to switch editions, choose their desired edition (CLASSIC or LITE), and confirm the switch by clicking the "Accept" button.

**Prerequisites:**

* Must have a Plex-Earth account.  
* Appropriate permissions to change plan settings.  
* You must be either on a free trial or an active subscription or currently using the LITE version.

## **Technical**

**Technical Details:**

* **Registry Storage:**  
  * The current edition will be stored as a string value in the "**EDITION**" key of the `Computer\HKEY_CURRENT_USER\Software\Plex-Earth 2025` path in the Windows Registry.  
  * Possible values are `CLASSIC` and `LITE`. If not set, it defaults to `CLASSIC`.  
  * Different installers for different editions should write the appropriate `EDITION` value in the Registry.  
  * Consideration is needed for cases where access to `HKEY_CURRENT_USER` is not allowed.  
* **C\# Class for Application Instances:**  
  * A new class will handle instances of applications for various editions.  
  * The class will include a `Current` property for the active Application instance.  
  * The class will have methods to `Switch` and `Migrate` to different editions.  
  * `Switch(string targetEdition)`: Creates an instance of the application specified in the `targetEdition` parameter.  
  * `Migrate(string targetEdition)`: Activates the user to the `targetEdition` application with their email and profile data, and then switches to it. During migration, the user will be prompted to confirm by entering a confirmation code received via email.  
* **Configuration Object in R1.Init File:**  
  * An object in the `R1.Init` file in the application's config will specify to which Editions and Service Plans each Application can be migrated.  
  * Whether an activation can be migrated will be controlled by a respective Permission value.  
  * A workstation/user-specific tag will control and apply any overrides.

**Performance Considerations:**

* **Registry Access:**  
  * Accessing and modifying the Windows Registry is generally a lightweight operation, but permissions and security settings might affect performance. Ensure error handling is in place for scenarios where access is restricted.  
* **Switching and Migrating Editions:**  
  * Switching and migrating editions involve creating instances and possibly performing network operations (e.g., email verification). These operations should be optimized for speed and efficiency.  
  * Ensure that the migration process, including sending and verifying confirmation codes, is streamlined to minimize delay and user frustration.  
* **Class Handling:**  
  * The new class handling application instances should be designed to manage resources efficiently. Proper disposal of instances and management of memory is crucial to prevent leaks and ensure smooth transitions.  
* **Config File Access:**  
  * Reading and writing to the `R1.Init` configuration file should be performed with care to avoid bottlenecks. Ensure that file I/O operations are optimized and do not block the main application thread.  
* **User Experience:**  
  * The user interface should provide feedback during the transition process to avoid the perception that the application is freezing or unresponsive. Loading indicators and progress messages can enhance the user experience.  
* **Testing and Monitoring:**  
  * Thorough testing is required to ensure the feature performs well under various conditions, such as different network speeds, system permissions, and user scenarios.  
  * Implement monitoring to track the performance of the switching and migration processes. Use analytics to identify and address any performance bottlenecks.


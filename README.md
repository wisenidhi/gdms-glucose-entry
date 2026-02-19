# gdms-glucose-entry
GDMS Glucose Entry Management - CS307 Assignment 2
# Gestational Diabetes Monitoring System (GDMS)

**307 Software Engineering – Assignment 2**  
**Student:** Nidhi Shree  
**Date:** February 9, 2026

---

## About This Feature

I am picking the Glucose Entry Management module, which was my user story 1 in the first assignment. The user story says: "As a patient, I want to enter a morning finger stick glucose value so that my CGM readings are calibrated accurately."

This feature is used by the patient to record the daily fasting blood glucose levels. Once this value is added into the data, it helps calibrate the CGM values recorded at the same time. This basic data entry is very important for CGM calibration, which in turn is important for accurate trend analysis and alerts. This feature is critical for usability as well as the safety of patient for accurate alerts.

Wrong glucose entries can mess up CGM data and lead to bad treatment decisions. This feature addresses the goals of accuracy and reliability directly.

---

## How to Run

This prototype used by me are HTML5, CSS3, and JavaScript. Idea is to just open `index.html` in a browser. Five sample entries load automatically aiding to test right away.

1. Download `gdms_glucose_entry.html`
2. Open it in Chrome
3. Five sample entries load automatically — you can start testing right away

---

## How It Works

The component diagram has three layers. First is User Interface, second is Logic and third is Data. Following the Model View Controller pattern, it helps organize software. It also makes it easy to maintain and test.

**UI Layer** has 3 parts:
- Glucose entry form to enter fasting blood sugar levels with editable timestamp
- Filter bar that has options to filter the view of entries as per priority or timestamp
- Entry list that displays saved entries and allows editing them

The UI layer only handles display and user input. It does not store data.

**Logic Layer** has the Entry Manager/Controller. This component controls how the system will behave. It receives input from the UI layer and applies business rules. It checks if there is duplicate entry on same day. It validates that glucose values are in safe range or not. It makes decision on saving or editing or deleting data. This layer is the bridge between the UI and the data layers.

**Data Layer** stores information on the glucose entry including its value, time and priority. It saves and returns data on request of the Entry Manager.

Data flows in direction of UI to logic layer to data layer and when updated it flows back to UI. The validation makes data trustworthy. Separation of layers makes data easy to maintain.

---

## Design Decisions

The MVC structure translated smoothly into code. The challenges I faced included that should I let patient choose priority level. Later I figured system chose priority automatically once set by provider. This reduces patient burden and aligns with varied preferences of different providers.

Other challenge was showing reviewed status clearly. Instead of using checkbox, I chose to highlight headings that are still to be reviewed.

The system does not let the patient make any duplicate entry for same day as patient only takes one fasting value everyday but it does allow to change the value or timestamp for correctness of data.

---

## Technologies Used

- HTML5
- CSS3
- JavaScript

---

## Testing

I created three main test cases and ran them manually in Chrome 131.

| ID | Test Case | Type | Expected Result | Result |
|---|---|---|---|---|
| TC01 | Add valid entry | Functional | Appears correctly | Pass |
| TC02 | Empty/invalid entry | Reliability | Rejected | Pass |
| TC03 | Delete entry | Functional | Removed from screen & storage | Pass |

Three test cases have passed. When a valid entry is added, it displayed the correct value and priority immediately. Invalid as well as empty entries were rejected with system giving a clear message. This helps keep the system trustworthy. When I tested by deleting an entry, I found it was deleted both from display section as well as storage section, which is what I wanted to keep data consistent.

Other tests that were performed were to check following:

1. Direct editing
2. Filtering by priority
3. Using the enter key to add entries

Everything worked properly on testing as I planned.

---

## What I Plan to Improve

- One thing we could do later is add keyboard shortcuts
- It would also be good to support screen readers and improve how the app updates using events
- I plan on adding automated testing with Jest or Mocha to catch bugs faster
- Cross browser testing for different browsers and mobile devices

---

## References

Fowler, M. (2004). *UML distilled: A brief guide to the standard object modeling language* (3rd ed.). Addison-Wesley.

Study.com. (2024). Requirements engineering, UML modeling, and agile planning lessons. https://study.com/

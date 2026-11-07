 <div align="center">

<a href="https://www.gohighlevel.com/" target="_blank" rel="noopener noreferrer">
  <img src="https://assets.cdn.filesafe.space/zELBHkVp0JPbbLvKIlF5/media/690a5f4a57ea175183408da2.png" alt="HighLevel Logo" width="260" />
</a>

**Powered by GoHighLevel**

A CRM, Lead Management, Appointment Automation and Patient Communication Portfolio Project.

[![Platform](https://img.shields.io/badge/Platform-GoHighLevel-286EF0?style=for-the-badge)](https://www.gohighlevel.com/)
[![Project](https://img.shields.io/badge/Project-Portfolio%20Demo-7C3AED?style=for-the-badge)]()
[![Workflows](https://img.shields.io/badge/Workflows-11%20Configured-16A34A?style=for-the-badge)]()
[![Testing](https://img.shields.io/badge/Testing-Partially%20Validated-EAB308?style=for-the-badge)]()

**Lead Management • Appointment Automation • Patient Communication • CRM Workflows**

</div>

---

## 1. Project Overview

Smile Dental CRM & Appointment Automation is a hands-on portfolio project built using **GoHighLevel (GHL)**.

The project demonstrates how a dental clinic can manage website enquiries, organize leads, automate appointment communications, handle patient replies, manage cancellations and no-shows, and coordinate front-desk follow-up activities.

The system includes **11 configured workflows** covering lead management, appointment lifecycle automation, patient communication, and post-appointment follow-up.

### Project Information

| Project Information | Details |
|---|---|
| Project Name | Smile Dental CRM & Appointment Automation |
| Platform | GoHighLevel |
| Project Type | Practice / Portfolio Demonstration |
| Business Type | Fictional Dental Clinic |
| Automation | GoHighLevel Workflows |
| Communication | Email and Internal Notifications |
| Calendar | Emily Front Desk's Personal Calendar |
| Workflow Count | 11 Configured Workflows |
| Production Status | Demo Only |

> This is an independent portfolio demonstration. It is not a live clinical system and does not process real patient information.

## 2. Business Requirements

The demo addresses common operational challenges in dental clinic management:

- Website enquiries requiring timely follow-up.
- Manual lead and opportunity management.
- Appointment confirmation and reminder communication.
- Appointment rescheduling and cancellation handling.
- Patient replies requiring staff attention.
- Missed appointments requiring follow-up.
- Post-appointment communication.
- Patient review requests.
- Double-booking prevention.

## 3. Proposed Solution

The project uses GoHighLevel CRM and Workflows to automate key business processes.

### Main Capabilities

- Website lead capture using contact tags.
- Automatic opportunity creation and task assignment.
- Lead acknowledgement and conditional follow-up emails.
- Appointment confirmation and reminder emails.
- Appointment rescheduling and cancellation handling.
- Patient reply detection and human handoff.
- No-show follow-up automation.
- Post-appointment thank-you communication.
- Automated review request emails.
- Front-desk notifications and follow-up tasks.
- Scheduled reminders for rescheduled appointments.
- Calendar availability validation through a double-booking test.

## 4. System Architecture

The following architecture illustrates the major components and automation flows implemented in the demo.

```mermaid
flowchart TB

    subgraph LEAD["01. LEAD MANAGEMENT"]
        direction TB
        A["Website Enquiry"]
        B["Contact Management"]
        C["Opportunity Creation"]
        D["Lead Follow-up Workflow"]
        E["Email and Staff Notification"]

        A --> B --> C --> D --> E
    end

    subgraph APPOINTMENT["02. APPOINTMENT LIFECYCLE"]
        direction TB
        F["Appointment Booking"]
        G["Appointment Confirmation"]
        H["Appointment Reminder"]
        I["Appointment Rescheduled"]
        J["Appointment Cancellation"]
        K["No-Show Automation"]
        L["Appointment Showed"]

        F --> G
        F --> H
        F --> I
        F --> J
        F --> K
        F --> L
    end

    subgraph COMMUNICATION["03. PATIENT COMMUNICATION"]
        direction TB
        M["Patient Email / SMS Reply"]
        N["Patient Reply Detection"]
        O["Needs Human Follow-up"]
        P["Front Desk Assignment"]
        Q["Follow-up Task"]
        R["Staff Notification"]

        M --> N --> O
        O --> P
        O --> Q
        O --> R
    end

    subgraph POST["04. POST-APPOINTMENT"]
        direction TB
        S["Post-Appointment Follow-up"]
        T["Review Request Automation"]
        U["Rescheduled Appointment Reminder"]

        L --> S
        L --> T
        I --> U
    end

    E -.-> F
```

## 5. Workflow Inventory

The project contains **11 configured GoHighLevel workflows**.

| # | Workflow | Purpose |
|---|---|---|
| 1 | New Website Lead Follow-up | Creates an opportunity and follow-up task when the website source tag is added. |
| 2 | Customer Follow-up | Sends acknowledgement and conditional follow-up emails based on opportunity stage. |
| 3 | Appointment Confirmation | Sends booking confirmation email and front-desk notification. |
| 4 | Appointment Reminder | Sends an appointment reminder one day before the scheduled appointment. |
| 5 | Appointment Rescheduled | Detects rescheduling and sends confirmation and staff notification. |
| 6 | Appointment Cancellation | Sends cancellation email and front-desk notification. |
| 7 | Patient Reply & Human Handoff | Detects email/SMS replies and assigns follow-up to the front desk. |
| 8 | No-Show Automation | Sends rescheduling email, creates a task, applies a tag, and notifies staff. |
| 9 | Post-Appointment Follow-up | Sends a thank-you email and creates a follow-up task. |
| 10 | Review Request Automation | Waits one day after appointment completion and sends a review request email. |
| 11 | Rescheduled Appointment Reminder | Uses an appointment-status trigger and rescheduled condition to schedule a reminder before the updated appointment. |

### Workflow Details

#### 1. New Website Lead Follow-up

**Trigger:** Contact Tag Added (`source_website`).

**Actions:**
- Create Opportunity.
- Create Follow-up Task.
- Notify Front Desk.

#### 2. Customer Follow-up

**Trigger:** Opportunity Created.

**Actions:**
- Send acknowledgement email.
- Wait one day.
- Check opportunity stage.
- Send conditional follow-up email if the opportunity remains in the configured New Lead stage.

#### 3. Appointment Confirmation

**Trigger:** Customer Booked Appointment.

**Actions:**
- Send confirmation email.
- Notify front-desk staff.

#### 4. Appointment Reminder

**Trigger:** Customer Booked Appointment.

**Actions:**
- Wait until one day before the appointment.
- Send appointment reminder email.

#### 5. Appointment Rescheduled

**Trigger:** Appointment Status.

**Condition:**
- `Rescheduled = True`

**Actions:**
- Send rescheduling confirmation email.
- Notify Front Desk.

#### 6. Appointment Cancellation

**Trigger:** Appointment Status — Cancelled.

**Actions:**
- Send cancellation email.
- Notify Front Desk.

#### 7. Patient Reply & Human Handoff

**Triggers:**
- Customer Replied — Email.
- Customer Replied — SMS.

**Actions:**
- Apply `Needs Human Follow-up` tag.
- Assign conversation to Front Desk.
- Create patient follow-up task.
- Notify Front Desk.

**Testing Note:** Email reply execution was tested successfully. SMS execution requires a configured phone number and messaging service.

#### 8. No-Show Automation

**Trigger:** Appointment Status — No-show.

**Actions:**
- Apply Appointment No-Show tag.
- Send rescheduling email.
- Notify Front Desk.
- Create No-Show Follow-up Task.

#### 9. Post-Appointment Follow-up

**Trigger:** Appointment Status — Showed.

**Actions:**
- Send post-appointment thank-you email.
- Create post-appointment follow-up task.

#### 10. Review Request Automation

**Trigger:** Appointment Status — Showed.

**Actions:**
- Wait one day.
- Send patient review request email.

**Testing Note:** Test email receipt was confirmed. A production review destination URL has not yet been configured.

#### 11. Rescheduled Appointment Reminder

**Trigger:** Appointment Status.

**Condition:**
- `Rescheduled = True`

**Actions:**
- Wait until one day before the updated appointment.
- Send rescheduled appointment reminder email.

**Testing Note:** The rescheduled branch was tested successfully, and the contact entered the scheduled Wait step. Final reminder email execution and delivery remain pending.

**Workflow Maintenance:** An older duplicate version of this workflow was moved to Draft after its two active test enrollments were removed. The newer final-tested version remains Published. The archived duplicate is not counted as an additional workflow.

## 6. Technology Stack

| Technology | Purpose |
|---|---|
| GoHighLevel CRM | Contact, opportunity and calendar management |
| GoHighLevel Workflows | Business process automation |
| Email Actions | Patient and lead communication |
| Internal Notifications | Front-desk alerts |
| GHL Calendar | Appointment scheduling |
| Conditional Branching | Workflow decision logic |
| Wait Actions | Time-based automation |

## 7. Testing & Validation

The following table summarizes the tests performed during the demo implementation.

| Workflow / Feature | Validation | Result |
|---|---|---|
| Appointment Confirmation | Test booking and confirmation email; appointment title, date and time content checked | Tested |
| Appointment Rescheduled | True and false branch execution | Passed |
| Appointment Cancellation | Cancellation email and notification actions | Passed |
| Appointment Reminder | One-day-before wait configuration | Configured; delivery verification pending |
| Customer Follow-up | Temporary one-minute wait test; restored one-day wait | Actions executed; inbox receipt not confirmed |
| New Website Lead Follow-up | Tag, opportunity, task and notification configuration | Published; detailed end-to-end validation pending |
| Patient Reply & Human Handoff | Email reply, tag, assignment, task and notification | Passed; SMS not tested |
| No-Show Automation | Tag, email action, task and notification | Actions executed; task and tag verified |
| Post-Appointment Follow-up | Thank-you email action and task creation | Actions executed; task verified |
| Review Request Automation | One-day wait and test email receipt | Passed |
| Rescheduled Appointment Reminder | Rescheduled condition and scheduled wait | Condition passed; final email delivery pending |
| Double Booking Test | Same calendar and same time slot with two contacts | Passed in the tested scenario |

### Double Booking Test

**Test Objective:** Verify whether the same calendar allows two appointments for the same time slot.

#### Test Configuration

| Parameter | Value |
|---|---|
| Calendar | Emily Front Desk's Personal Calendar |
| Date | November 9, 2026 |
| Time Slot | 11:00 AM – 11:30 AM CST |
| Contact A | Double Booking A |
| Contact B | Double Booking B |

#### Test Results

1. Contact A successfully booked the selected slot.
2. Contact B was selected for the same date and calendar.
3. The 11:00 AM – 11:30 AM slot was not available in the second booking form.
4. A later slot was displayed instead.

**Result:** The tested calendar prevented the second booking for the same time slot.

> This is a successful functional test of the tested scenario, not a guarantee against every possible concurrent-booking race condition.

### Important Testing Notes

- An `Executed` workflow action indicates that GHL executed the action; it does not independently prove inbox delivery.
- Email receipt was confirmed for the Review Request test.
- Patient Reply & Human Handoff actions were verified through execution logs.
- SMS was not fully tested because no phone number was configured for messaging.
- The appointment reminder's actual delivery and appointment date/time merge fields require further verification.
- Rescheduled Appointment Reminder enrollment was verified, but final reminder email execution and delivery remain pending.
- The project uses synthetic test contacts.

### Historical Workflow Enrollment Snapshot

The earlier workflow overview captured the following enrollment counts for the original six-workflow configuration.

| Workflow | Total Enrolled | Active Enrolled |
|---|---:|---:|
| Appointment Cancellation | 1 | 0 |
| Appointment Confirmation (Practice) | 7 | 0 |
| Appointment Reminder | 1 | 1 |
| Appointment Rescheduled | 15 | 0 |
| Customer Follow-up (Practice) | 2 | 1 |
| New Website Lead Follow-up | 5 | 0 |

These are historical, point-in-time demo counts from the earlier workflow configuration. They are not current counts for all 11 workflows, performance metrics, or evidence of patient outcomes.

## 8. Project Screenshots

The repository contains the actual workflow screenshots under the `screenshots/workflows/` directory.

### Workflow Overview

![Workflow Overview](screenshots/workflows/00-workflow-overview.png)

### 1. Appointment Confirmation

![Appointment Confirmation](screenshots/workflows/01-appointment-confirmation.png)

### 2. Appointment Reminder

![Appointment Reminder](screenshots/workflows/02-appointment-reminder.png)

### 3. Appointment Rescheduled

![Appointment Rescheduled](screenshots/workflows/03-appointment-rescheduled.png)

### 4. Appointment Cancellation

![Appointment Cancellation](screenshots/workflows/04-appointment-cancellation.png)

### 5. Customer Follow-up

![Customer Follow-up](screenshots/workflows/05-customer-follow-up.png)

### 6. New Website Lead Follow-up

![New Website Lead Follow-up](screenshots/workflows/06-new-website-lead-follow-up.png)

### 7. Patient Reply & Human Handoff

![Patient Reply and Human Handoff](screenshots/workflows/07-patient-reply-human-handoff.png)

### 8. No-Show Automation

![No-Show Automation](screenshots/workflows/08-no-show-automation.png)

### 9. Post-Appointment Follow-up

![Post-Appointment Follow-up](screenshots/workflows/09-post-appointment-follow-up.png)

### 10. Review Request Automation

![Review Request Automation](screenshots/workflows/10-review-request-automation.png)

### 11. Rescheduled Appointment Reminder

![Rescheduled Appointment Reminder](screenshots/workflows/11-rescheduled-appointment-reminder.png)

## 9. Project Outcomes

This project demonstrates practical experience with:

- CRM contact and opportunity management.
- Multi-step workflow configuration.
- Appointment lifecycle automation.
- Conditional branching and time-based waits.
- Email communication automation.
- Internal notifications and task creation.
- Human handoff and staff assignment.
- No-show and review-request automation.
- Rescheduled appointment reminder scheduling.
- Calendar availability validation.
- Workflow enrollment and execution-log analysis.

## 10. Production Readiness & Security

This is a portfolio demonstration, not a production clinical application.

Before adapting the system for a real dental clinic:

- Configure a dedicated clinic calendar and approved staff schedules.
- Configure a verified email sending domain.
- Validate all appointment merge fields and actual email delivery.
- Configure an approved SMS provider and consent-based messaging.
- Implement opt-out handling.
- Use role-based access and least-privilege permissions.
- Protect patient and contact information.
- Avoid including sensitive health information in general-purpose automation messages.
- Implement duplicate-event handling, retries and monitoring.
- Test appointment conflicts, reschedules, cancellations and workflow re-entry.
- Review applicable privacy, security and healthcare compliance requirements.

**No HIPAA compliance or production deployment is claimed for this demo.**

## 11. Future Enhancements

1. Dedicated clinic calendar configuration.
2. Verified email domain and deliverability monitoring.
3. SMS and WhatsApp integration with consent and opt-out handling.
4. Advanced appointment conflict and concurrency testing.
5. Workflow error handling and recovery procedures.
6. Lead assignment and overdue follow-up alerts.
7. Reporting dashboard for leads and appointment performance.
8. Automated suppression of outdated reminders after appointment changes.
9. More comprehensive integration and regression testing.

## 12. Setup Overview

This repository documents workflow design, implementation and testing evidence. It does not contain importable GoHighLevel workflow exports or account credentials.

To recreate the demo:

1. Configure a GoHighLevel test location.
2. Create a test pipeline and opportunity stages.
3. Configure the required contact tags.
4. Configure a test calendar and team member.
5. Create the 11 workflows described in this README.
6. Configure email actions and internal notifications.
7. Configure the required triggers, conditions and wait actions.
8. Run test cases using synthetic contacts.
9. Inspect Enrollment History and Execution Logs.
10. Verify email delivery separately from workflow execution.
11. Document the results and screenshots.

## 13. Author

**Aminul Islam**

Software Developer | Oracle APEX & Database Development | CRM and AI Workflow Automation

- **GitHub:** [Aminul-Eng](https://github.com/Aminul-Eng)
- **Portfolio:** [aminulaicloud.com](https://aminulaicloud.com)
- **Project Repository:** [smile-dental-crm-automation](https://github.com/Aminul-Eng/smile-dental-crm-automation)

## 14. Platform Branding

This project uses the GoHighLevel platform for demonstration purposes. HighLevel and its logo are trademarks of their respective owner. This independent portfolio project is not sponsored, endorsed or certified by HighLevel.

The HighLevel logo is used to identify the platform used in this demonstration.

## 15. Disclaimer

This project is an independent practice and portfolio demonstration. It is not an official GoHighLevel product, is not affiliated with or endorsed by GoHighLevel, and is not a live clinical system.

“Smile Dental” is a fictional demo business name. Do not use this demonstration as-is to process real patient information.

---

<div align="center">

**Built as a practical demonstration of CRM, appointment and business process automation using GoHighLevel.**

</div>

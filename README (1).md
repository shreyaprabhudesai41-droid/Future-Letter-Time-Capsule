# Future Letter -- Your Time Capsule

A time-delayed digital letter project built with **n8n** and **Gmail**.
Users can write a letter to their future selves, choose when it should
be delivered, and receive it by email at the selected time. The workflow
can also send attachments when photos or videos are included.

## 🎥 Project Demo Video

**Google Drive video link:**\
`PASTE_YOUR_GOOGLE_DRIVE_VIDEO_LINK_HERE`

Replace the placeholder above with your Google Drive share link. Set the
video's sharing permission to **Anyone with the link -- Viewer** if you
want others to watch it.

## ✨ Features

-   Collects time-capsule details through an n8n form.
-   Calculates the scheduled delivery time.
-   Waits until the selected delivery time.
-   Sends the letter to the recipient's email address using Gmail.
-   Checks whether photos or videos are attached.
-   Uses separate email paths for letters with attachments and text-only
    letters.
-   Personalizes the email greeting using the recipient's name.
-   Sends the email with **Future Letter** as the sender name.

## 🔄 Workflow

1.  **Time Capsule Form** -- Collects the letter details.
2.  **Calculate Delivery Time** -- Calculates the time when the letter
    should be delivered.
3.  **Wait Until Delivery Time** -- Holds the workflow until the
    scheduled delivery time.
4.  **Has Photos or Videos?** -- Checks whether the submission includes
    attachments.
5.  **Send Capsule With Files** -- Sends the letter and attachments when
    files are present.
6.  **Send Capsule Text Only** -- Sends the letter without attachments
    when no files are present.

### Workflow overview

``` text
Time Capsule Form
        |
        v
Calculate Delivery Time
        |
        v
Wait Until Delivery Time
        |
        v
Has Photos or Videos?
       / \
    Yes   No
     |     |
     v     v
Send with  Send text
attachments only
```

## 🧰 Requirements

-   An n8n instance (cloud or self-hosted).
-   A Google account.
-   Gmail credentials connected to n8n.
-   The workflow JSON exported from n8n.

## ⚙️ Setup Instructions

1.  Open your n8n workspace.
2.  Import the workflow JSON file.
3.  Open both Gmail nodes:
    -   **Send Capsule With Files**
    -   **Send Capsule Text Only**
4.  Select or create Gmail OAuth2 credentials for each node.
5.  Check the form fields and confirm that the field names match the
    expressions used in the workflow, such as `name`, `email`,
    `subject`, `writtenOn`, and `message`.
6.  Confirm that the delivery-time calculation uses the selected
    delivery date and time from the form.
7.  Check how attachments are supplied. The attachment property must
    refer to a valid **binary property name** available in the incoming
    n8n item.
8.  Test with a text-only letter using your own email address.
9.  Test again with an attachment, then verify that the correct Gmail
    node runs.
10. Activate the workflow when testing is complete.

> **Important:** The provided workflow snippet references
> `attachmentKeys` for the Gmail attachment property. In n8n, Gmail
> attachments normally need to point to the relevant binary property
> name(s) on the incoming item. Verify that the form/upload step
> actually creates those binary properties and that `attachmentKeys`
> contains the expected value.

## 🧪 Testing Checklist

-   [ ] The form accepts the required letter details.
-   [ ] The recipient email address is correct.
-   [ ] The chosen delivery date and time are calculated correctly.
-   [ ] The workflow waits until the intended delivery time.
-   [ ] A text-only letter is sent through **Send Capsule Text Only**.
-   [ ] A letter with photos or videos is sent through **Send Capsule
    With Files**.
-   [ ] The email subject, greeting, letter text, and sender name look
    correct.
-   [ ] Attachments arrive and can be opened.

## 🔐 Privacy and Safety

-   Only send letters to email addresses that the user is authorized to
    use.
-   Avoid putting passwords, API keys, OAuth tokens, or other secrets in
    the workflow export or repository.
-   Be careful when sharing example letters or uploaded media because
    they may contain personal information.
-   Test delivery using an email address you control before enabling the
    workflow for other users.

## 🛠️ Troubleshooting

**The email is not sent** - Check that Gmail credentials are connected
and authorized. - Review the execution details in n8n for errors. -
Verify that the `email` and `subject` fields contain valid values.

**The letter arrives at the wrong time** - Check the delivery-time
calculation and the timezone used by the workflow. - Test with a
delivery time a few minutes in the future.

**The attachment is missing** - Confirm that the incoming item contains
the uploaded file as binary data. - Verify the binary property name
configured in the Gmail node. - Check that the attachment branch is
receiving the expected item.

**The workflow does not continue after waiting** - Check the execution
status and your n8n deployment's execution settings. - Ensure the
workflow is saved and configured correctly.

## 📌 Project Summary

**Future Letter -- Your Time Capsule** lets users send a personal
message into the future. By combining an n8n workflow, scheduled
waiting, and Gmail delivery, it turns a written reflection into a
time-delayed email experience.

------------------------------------------------------------------------

*Project documentation: update this README if the form fields, node
names, or attachment handling change.*

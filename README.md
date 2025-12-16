# FB-E164-Phone-Cleaner
PHP solution for JetFormBuilder that implements rigorous cleaning (Custom Transform) of the Phone field. It removes formatting characters (parentheses, hyphens, spaces) to ensure that data is sent in E.164 format (e.g., +15551234567) to webhooks from services such as Twilio and Make, preventing failures in SMS automations.

# 📞 Solution: E.164 Cleaning for Phone Field in JetFormBuilder
This repository documents a solution to the common problem of sending phone number data with input masking (e.g., `+1 (555) 123-4567`) to services that require the international **E.164** format (e.g., `+15551234567`), such as Twilio or SMS gateways, when using Webhooks with **Make (Integromat)**.

The solution is implemented using JetFormBuilder's (JFB) **`Custom Transform`** functionality.

## 1. ⚠️ The Problem
When using a `Tel` field in JetFormBuilder with an **Input Mask**, JFB stores and sends the value **with formatting characters** (spaces, hyphens, parentheses) through the Webhook.

This causes services such as Twilio (for sending confirmation SMS) to reject the request, as it does not adhere to the strict E.164 format, causing constant failures in Make automation.

## 2. ✅ The Solution: Custom Transform (PHP)
Instead of relying on JFB's standard sanitization options, we created a custom PHP function that rigorously cleans the data to leave only the `+` sign and digits.

### Step A: Add the PHP Function (To the Server)
Copy and paste the following PHP code into the `functions.php` file of your child theme or using a code snippet plugin.

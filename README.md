# FB-E164-Phone-Cleaner
PHP solution for JetFormBuilder that implements rigorous cleaning (Custom Transform) of the Phone field. It removes formatting characters (parentheses, hyphens, spaces) to ensure that data is sent in E.164 format (e.g., +15551234567) to webhooks from services such as Twilio and Make, preventing failures in SMS automations.

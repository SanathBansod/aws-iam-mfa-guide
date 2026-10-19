# AWS IAM Multi-Factor Authentication (MFA)

A screenshot-based walkthrough for enabling Multi-Factor Authentication (MFA) in AWS using an authenticator app.

> **Security warning:** Never publish an MFA QR code, TOTP secret key, one-time password (OTP), password, access key, or unredacted AWS account details. Review every screenshot before making this repository public. Redact any sensitive value first.

## What is MFA?

Multi-Factor Authentication adds a second verification step to sign-in. In addition to a password, the user provides a time-based one-time password (TOTP) from an authenticator app or uses another supported MFA method.

## Prerequisites

- Access to the AWS account and appropriate permissions to manage MFA.
- A compatible authenticator app, such as Google Authenticator, Duo Mobile, or another compatible TOTP app.
- A secure recovery plan that follows your organization's account policy.

## Step 1 — Open IAM and select Add MFA

Open the AWS Management Console and navigate to **IAM**. On the IAM dashboard, select **Add MFA** for the root user if that is the identity you intend to secure.

![AWS IAM dashboard with Add MFA highlighted](screenshots/01-iam-dashboard.jpg)

**Note:** Root-user MFA protects the root user. To secure an IAM user instead, open that user's security credentials and configure MFA for that specific user.

## Step 2 — Name the device and choose Authenticator app

Enter a recognizable device name, then select **Authenticator app** from the available MFA device options.

![MFA device name and authenticator app selection](screenshots/02-mfa-device-selection.jpg)

Use a descriptive label only; never place a password or secret in the device name.

## Step 3 — Register the authenticator app

Follow the AWS setup page to display the QR code and scan it using your authenticator app. If scanning is unavailable, AWS may offer a secret-key option.

![Authenticator app registration screen](screenshots/03-authenticator-app-setup.jpg)

- Keep the QR code and secret key private. Anyone who obtains the TOTP secret may be able to generate codes for that MFA device.
- Enter the current code from your authenticator app when prompted.
- If AWS requests two consecutive codes, wait for the app to generate the next code and enter it as instructed.
- Finish the AWS console flow and verify that the MFA device is registered.

## Verification checklist

- [ ] The intended identity (root user or IAM user) was selected.
- [ ] The authenticator app was registered successfully.
- [ ] AWS confirms that the MFA device is assigned.
- [ ] Sign-in works with the configured second factor.
- [ ] Recovery information is stored securely according to account policy.

## Troubleshooting

- **Code rejected:** Check that your device time is set automatically, use a fresh code, and confirm that you selected the correct authenticator entry.
- **QR code cannot be scanned:** Use manual entry only if AWS presents a secret key, and keep that key confidential.
- **Lost device:** Follow your account's recovery or MFA replacement procedure.

## Disclaimer

This is an educational walkthrough. Console labels and workflows may change over time.

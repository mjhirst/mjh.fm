---
layout: post
title:  "I Love Certificates"
date:   2023-02-10 21:22:54 +0000
categories: tech
---
I'm the only person at work who uses GPG and S/MIME. I found it fascinating and slightly reassuring that I could suddenly 'sign' things, like my git commits and get a green _verified_ pill on GitHub. S/MIME I thought would have been very useful when emailing with my solicitor. So I looked for a free setup (by the way, the Italian CA Actalis offer [S/MIME certs for free](https://extrassl.actalis.it/portal/uapub/freemail?lang=en)) Y'know, to encrypt emails and sensitive attachments. I was a bit disappointed to learn they would just send a PDF document with a password in a second email. And then that password would be wrong. For now, S/MIME seems reserved for the big corps and bug-bounty programmes.

I use GPG with [GPG Suite for Mac](https://gpgtools.org/) to visually manage the interface. It's usually pretty seamless if you remember to not install the GPG helper for mail. I have had a few issues where my computer would suddenly stop signing my commits in the middle of the workday. Nothing a reboot couldn't solve.

Here's my fingerprint:
```
  B268 CCC7 B562 AFCF 227F
  C9C0 58EE BB95 5937 7D25
```

You _can_ sign Git commits with GPG, SSH and/or S/MIME with GitHub. I tend to keep my SSH certificates to connect to things. And the S/MIME needs an external CA. So GPG feels like it's 'mine' since I can generate it all locally.

Traditionally, SSH is used for connections, S/MIME for documents and GPG for, well, signing Git commits. SSH is designed to give you secure access to the repository but doesn't confirm identity. Using GPG to sign a commit helps produce a SHA1 hash for that commit to demonstrate it wasn't tampered with.

1. To sign commits by default
  ```
    git config --global commit.gpgsign true
  ```
2. Generate the key if you haven't already and list them out with
  ```
    gpg --list-secret-keys --keyid-format=long
  ```
3. From the output, you'll want to use the first line of `sec` after the key type (which could be `4096R` or `ed25519` followed by a `/`) and use the 16-digit ID like `05XD36X5E8XXF35X`. Then tell git about that key.
  ```
    git config --global user.signingkey 05XD36X5E8XXF35X
  ```
Of course, [GitHub](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key) has a great writeup, a few more troubleshooting steps and also how to go about using your SSH key instead.

 git config --global url.ssh://git@github.com/.insteadOf https://github.com/
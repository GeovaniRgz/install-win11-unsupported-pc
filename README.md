# 🚫 TPM? No Problem: Install Windows 11 on Unsupported PCs (Free, Easy, and No Extra Software)

## 🧠 Why This Exists

Hey! 👋 I made this repo because I’ve seen way too many people struggling to install **Windows 11 on older PCs** that are still perfectly fine.

Most guides online tell you to download weird tools or even pay for software just to create a bootable USB. No thanks. 🙅‍♂️

This method is **100% free**, safe, and uses only **official Microsoft tools**, the only thing you’ll add is one small file: `autounattend.xml`.

---

## ⚠️ Before We Start: What’s This About?

This guide is for you if:
- Your PC is "unsupported" (no TPM, old CPU, not enough RAM, etc.)
- You don’t want to pay for tools or modify an ISO
- You just want to install **vanilla Windows 11** and do the cleanup later

If you’re looking for a super-customized installer that removes bloatware and tweaks privacy settings, check other projects on GitHub. This one keeps it simple and clean.

---

## 🤔 What is `autounattend.xml` (and what it does *not* do)

Think of `autounattend.xml` as a little helper script for Windows Setup.

When you boot from a USB, Windows looks for this file to see if it should skip or automate certain steps. In our case, it quietly tells Windows:

> "Hey, don’t worry about TPM, Secure Boot, RAM, storage, CPU, or disk checks. Just install like normal."

That's it! No hacks, no shady software. Windows setup just skips the checks and installs like usual.

> **💡 Note:** This file does **not** fully automate the Windows installation. You’ll still go through the normal setup screens, choose partitions, editions, and configure everything yourself. The only thing it does automatically is insert registry keys before installation to skip unsupported hardware checks.

---

## 🛠️ How to Use It (Step-by-Step)

### 1. Grab a USB Drive
- Minimum **8GB**.
- Make sure it’s **empty**, you’ll be formatting it.

### 2. Download the Official Windows 11 Tool
Go to the official Microsoft site:
➡️ [Download Windows 11](https://www.microsoft.com/en-gb/software-download/windows11)

Under **"Create Windows 11 Installation Media"**, click **Download Now** and run the tool. Follow the steps to create a bootable USB with Windows 11.

### 3. Add the `autounattend.xml` File
- Download or clone this repo
- Copy the `autounattend.xml` file to the **root** (main) folder of the USB you just created  
🧠 Make sure it’s not inside a subfolder!

### 4. Boot and Install!
- Restart your PC
- Boot from the USB (you might need to hit F12, F2, ESC, or DEL to access boot options)
- Windows 11 will now install without complaining about "unsupported hardware" 🎉

---

## ✅ Optional: Skip Microsoft Account Requirement

If you want to **install without internet** and skip Microsoft account login:

1. At the "Let’s connect you to a network" screen, press `Shift + F10`
2. In the command prompt, type: `OOBE\BYPASSNRO`
3. Your PC will restart. When it gets back to the network screen, now you’ll see **“I don’t have internet”** → choose that and set up a local account.

---

## 🧪 What the XML File Does (Behind the Scenes)

This file tells Windows Setup to add the following registry values during the initial phase (Windows PE):

| Bypass Check        | What It Skips                         |
|---------------------|----------------------------------------|
| `BypassTPMCheck`     | No TPM module required                |
| `BypassSecureBootCheck` | No Secure Boot needed             |
| `BypassStorageCheck` | Skips storage requirement check       |
| `BypassCPUCheck`     | Installs even on unsupported CPUs     |
| `BypassRAMCheck`     | Ignores minimum RAM check             |
| `BypassDiskCheck`    | Doesn’t care about disk type (HDD/SSD)|

All of this happens automatically, without asking you anything.

---

## 🧼 About Privacy and Bloatware

This XML doesn’t touch privacy settings, telemetry, or uninstall apps. I prefer to do all of that **manually after installation**, so I know what’s going on.

If you’re looking for a version that does tweaks and removes built-in junk automatically, I might share a personal version later, let me know if you’re interested.

---

## 🎉 That’s It!

You now have a quick, clean, and **free** way to install Windows 11 on your “unsupported” PC, no shady tools, no modified ISOs, just one smart file and the official Microsoft tool.

Enjoy!  
– Geovani ☕
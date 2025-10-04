# ☁️ 01 — Setup Your Azure Subscription

> 🎯 **Goal:** Create and prepare your Azure environment for the Honeypot Lab.

---

## 🪄 Step 1: Sign in to Azure
👉 Go to [**Azure Portal**](https://portal.azure.com) and sign in with your Microsoft account.

If you don’t have one yet:
- ✨ [**Create a Free Azure Account**](https://azure.microsoft.com/en-us/free/)  
  You’ll get **$200 credit for 30 days** and 12 months of free services!
- Or use a **paid subscription** if you already have credits (just remember to clean up resources later).

---

## 💳 Step 2: Verify Subscription
Once logged in:
1. Click on **☰ Menu → Subscriptions**  
2. Confirm you have at least one **Active Subscription**
3. Copy or note your **Subscription ID** (you’ll need it for screenshots/documentation)

📝 *Example Screenshot:*  
_Add this image in your repo later as_  
`docs/screenshots/01-azure-subscription.png`  

---

## 🧩 Step 3: Create a Resource Group
It’s best to keep all lab assets in one group.

1. In Azure Portal, search **Resource groups**
2. Click **+ Create**
3. Give it a name like `HoneypotLab-RG`
4. Choose your subscription and region (example: East US)
5. Click **Review + Create → Create**

✅ This makes it super easy to delete everything when you’re done testing.

---

## 🧹 Tips for Better Management
- 🏷️ **Use Tags**: e.g.,  
  - `Environment = Lab`  
  - `Owner = YourName`  
  - `Purpose = Honeypot`  
  Helps with billing & filtering resources later.
- 🧨 **Cleanup Tip**: After your experiment, go to **Resource Groups → HoneypotLab-RG → Delete resource group** to remove all resources in one click.
- 💰 **Cost Control**: Stop the VM when you’re not using it to avoid credit burn.

---

## 🧠 Quick Recap
| Step | Action | Outcome |
|------|---------|----------|
| 1️⃣ | Log in to [portal.azure.com](https://portal.azure.com) | Access Azure Dashboard |
| 2️⃣ | Create or verify your subscription | Ready to deploy resources |
| 3️⃣ | Create Resource Group | Organize all lab assets neatly |

---

🎉 **Next:** Move on to [02 - Create Honeypot VM](02-create-vm.md) to build your first attack surface!

To "get more space" in GitHub Codespaces, it depends on whether you are running out of **disk space inside your current project** (getting "No space left on device" errors) or if you have hit your **monthly account storage limit** (the 15GB free tier cap).

Here is the solution for both scenarios.

### Scenario A: Your Current Codespace is Full ("No Space Left on Device")

If you are seeing errors while installing packages or downloading files, your virtual machine's hard drive is full. You have two options:

#### Option 1: Upgrade the Machine Type (Recommended)

You can switch your Codespace to a larger machine. Higher-tier machines often come with larger hard drives (e.g., jumping from 32GB to 64GB or 128GB).

1.  Open your Codespace.
2.  Press `F1` (or `Ctrl`+`Shift`+`P`) to open the Command Palette.
3.  Type and select: **`Codespaces: Change Machine Type`**.
4.  Select a machine with higher specs (e.g., **4-core** or **8-core**).
      * *Note: This will restart your Codespace and may use your free usage hours faster.*

#### Option 2: Clean Up Disk Space

If you cannot upgrade, run these commands in your Codespace terminal to delete temporary files:

  * **Remove unused packages:**
    ```bash
    sudo apt-get clean
    sudo apt-get autoremove
    ```
  * **Clear Docker cache (often the biggest space hog):**
    ```bash
    docker system prune -a
    ```
    *(Type `y` when prompted. This deletes unused containers and images.)*

-----

### Scenario B: Your GitHub Account Storage is Full (15GB Limit)

GitHub provides **15GB of storage per month** for free. This counts every Codespace you have created, even if you aren't currently running them. If you hit this limit, you cannot create new Codespaces.

#### 1\. Delete Unused Codespaces

This is the fastest way to free up account space.

1.  Go to the [GitHub Codespaces Dashboard](https://github.com/codespaces).
2.  Identify old Codespaces you no longer need.
3.  Click the **... (three dots)** button next to the Codespace.
4.  Select **Delete**.

#### 2\. Lower the Retention Period

By default, GitHub keeps stopped Codespaces for 30 days, eating up your storage quota. Lower this to auto-delete them sooner.

1.  Go to your GitHub **Settings**.
2.  On the left sidebar, click **Codespaces**.
3.  Under "Default retention period," change it from **30 days** to **1 day** or **3 days**.

### Summary Checklist

| Problem | Symptom | Fix |
| :--- | :--- | :--- |
| **VM Disk Full** | "No space left on device" error in terminal | **Change Machine Type** to 8-core or run `docker system prune` |
| **Account Quota Full** | Cannot create new Codespace / Billing warning | **Delete old Codespaces** on dashboard & reduce retention period |

**Next Step:** Would you like me to show you how to check exactly how much storage your current Codespace is using via the terminal?

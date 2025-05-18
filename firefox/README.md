To **close all Firefox windows at once** via the command line on **Ubuntu 22.04**, you can use the `pkill` command, which kills all processes with a given name:

### ✅ Command:

```bash
pkill firefox
```

This will **terminate all running Firefox processes**, closing all windows and tabs.

---

### 🧠 Additional Tips:

* **Restoring previous session:**
  Since you've enabled the setting `Open previous windows and tabs`, Firefox will restore your previous session the next time you open it **only if it's shut down cleanly**. Using `pkill` is generally safe for this, but if you're concerned about a "clean" shutdown (for session restoration), use:

  ```bash
  pkill -SIGTERM firefox
  ```

  This sends the `SIGTERM` signal, which gives Firefox a chance to clean up before exiting. Avoid using `SIGKILL` (`-9`) as it forces an immediate shutdown, potentially skipping session save.

---

### 💡 Optional: Check it's fully closed

After running the command, verify that all processes are closed:

```bash
pgrep firefox
```

If it returns nothing, Firefox is fully closed.

Let me know if you'd like a script to automate this or handle other apps similarly.


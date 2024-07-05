# To connect to a remote server and launch multiple tasks
To achieve what you're aiming for—running multiple commands in parallel on a remote machine and being able to disconnect from your laptop while these commands continue running—you can use the `screen` command effectively. Here's a step-by-step guide on how to do this:

### Steps to Run Commands in Parallel Using `screen`:

1. **SSH into the Remote Machine:**
   First, you need to connect to the remote machine using SSH.
   ```bash
   ssh username@remote_machine_ip
   ```

2. **Start a `screen` Session:**
   Once logged in, start a new `screen` session.
   ```bash
   screen -S session_name
   ```
   Replace `session_name` with a meaningful name for your session. This helps you identify the session later.

3. **Run Commands in New `screen` Windows:**
   - To open a new window within `screen`, press `Ctrl` + `a`, release them, and then press `c`.
   - In the new window, you can run your first command.
   - Repeat the `Ctrl` + `a`, `c` sequence to create additional windows and run the other commands. You can have up to four commands running in separate windows.

4. **Navigating Between Windows in `screen`:**
   - To switch between `screen` windows, use `Ctrl` + `a`, followed by `n` for the next window or `p` for the previous window.

5. **Detach from the `screen` Session:**
   - You can detach from the `screen` session without stopping the running commands by pressing `Ctrl` + `a`, then `d`. This will take you back to the shell, but the commands continue to run in the background within the `screen` session.

6. **Log Out from SSH:**
   - You can now safely log out of the SSH session without interrupting your commands.
   ```bash
   exit
   ```

7. **Reattach to the `screen` Session Later:**
   - When you log back into the remote machine and want to reattach to your `screen` session, use:
     ```bash
     screen -r session_name
     ```
   - If you forget the session name, you can list all available `screen` sessions with:
     ```bash
     screen -ls
     ```
   - Then reattach using the session ID provided.

### Example Workflow:

1. SSH into your remote machine:
   ```bash
   ssh user@remote_machine
   ```

2. Start a `screen` session named `parallel_tasks`:
   ```bash
   screen -S parallel_tasks
   ```

3. Open the first window and run your command:
   ```bash
   ./command1.sh
   ```

4. Create a new window and run the next command:
   ```bash
   Ctrl + a, c
   ./command2.sh
   ```

5. Repeat for the remaining commands:
   ```bash
   Ctrl + a, c
   ./command3.sh
   Ctrl + a, c
   ./command4.sh
   ```

6. Detach from the `screen` session:
   ```bash
   Ctrl + a, d
   ```

7. Log out from SSH:
   ```bash
   exit
   ```

8. To reconnect later:
   ```bash
   ssh user@remote_machine
   screen -r parallel_tasks
   ```

This setup allows your commands to run independently in separate `screen` windows, and they will continue to execute even after you disconnect from the SSH session.
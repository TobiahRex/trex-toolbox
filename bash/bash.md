# Bash
[Home](../README.md)


1. Open screen documentation
   ```bash
   screen docs
   ```

2. Run a script and print output to a log file while disconnecting
   ```bash
   nohup <script> > <log file> &
   # Replace <script> with the script you want to run and <log file> with the desired log file name.
   ```

3. Show active screen sessions
   ```bash
   screen ls
   ```

4. Run a Python script with a flag and output to a log file while disconnecting
   ```bash
   nohup python -u main.py --some-flag > some-log.log &
   # Replace main.py with your script name and --some-flag with the desired flag.
   ```

5. Reconnect to a screen session
   ```bash
   screen -R <id>
   # Replace <id> with the screen session ID.
   ```

6. Show the end of a file and follow appends to the file
   ```bash
   tail -f <log file>
   # Replace <log file> with the name of the log file you want to view.
   ```

7. Show the last 50 lines of a file
   ```bash
   tail -50 <log file>
   # Replace <log file> with the name of the file you want to view.
   ```

8. Inspect a file using the `less` command
   ```bash
   less <log file>
   # Replace <log file> with the name of the file you want to inspect.
   ```

9. Search for a specific string in a file using `less`
   ```bash
   less <log file>
   # Press / and enter the string you want to search for in the log file.
   ```

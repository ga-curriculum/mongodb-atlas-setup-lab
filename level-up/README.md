# ![MongoDB Atlas Setup Lab - Level Up](./assets/hero.png)

## Test Drive in the Mongo Shell

Click the **Connect** button again on the **Overview** page, and this time select **Shell** under the **Access your data through tools** header:

![Atlas Shell](./assets/shell.png)

Although Atlas may show how to permanently install `mongosh` (MongoDB's Shell) for your operating system, **it is unnecessary.**

Instead, we can temporarily install and run `mongosh` by copying and pasting the command shown in Atlas into **Terminal**.

![Atlas Shell Connection](./assets/shell-connection.png)

❗️ Before pressing enter, add `npx` to the front of the command so that the command looks something like this:

```bash
npx mongosh "mongodb+srv://student-cluster.uwdsn12.mongodb.net/" --apiVersion 1 --username <yourusername>
```

If prompted to install, be sure to answer with `y`.

You will be prompted to enter your **database user's** password.

Congrats, you are now ready to test your databases! 🎉

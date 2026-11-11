# GitHub Exercises

Do these exercises **in your own fork** of this repository. By the end you will have practiced forking, branching, pull requests, issues, and resolving merge conflicts.

## Setup: Fork and clone

1. Click the **Fork** button at the top of this page and fork the repository to your own account.
2. Clone *your* fork (replace `YOUR-USERNAME`):

   ```bash
   git clone https://github.com/YOUR-USERNAME/github-workshop.git
   cd github-workshop
   ```

3. Check your remotes — `origin` should point at *your* fork:

   ```bash
   git remote -v
   ```

> Only `origin` (your fork) is needed for these exercises. Syncing with the original repository is covered in Exercise 4.

## Exercise 1 — Branch, commit, pull request

You'll add your GitHub username to `CONTRIBUTORS.md`.

1. Create and switch to a new branch:

   ```bash
   git checkout -b add-my-name
   ```

2. Add your GitHub username as a new bullet at the bottom of the list in `CONTRIBUTORS.md` (edit the file by hand, or):

   ```bash
   echo "- YOUR-USERNAME" >> CONTRIBUTORS.md
   ```

3. Commit and push your branch:

   ```bash
   git add CONTRIBUTORS.md
   git commit -m "Add YOUR-USERNAME to contributors"
   git push -u origin add-my-name
   ```

4. GitHub will print a link to **open a pull request** — follow it, or open one from the **Pull requests** tab. Your PR targets `main` of *your fork*.

5. Review the **Files changed** tab — this diff is exactly what a reviewer sees. Then click **Merge pull request**.

✅ You should now see your name in `CONTRIBUTORS.md` on `main`.

## Exercise 2 — Issues

Good projects use issues to track work and discussion.

1. Open the **Issues** tab of your fork and comment on the issue titled **"Introduce yourself! 👋"** — say hi with your GitHub username, and mention someone with `@`.
2. Give someone's comment a 👍 reaction.
3. Open a **new issue** of your own. Ideas:
   - A typo you spotted
   - A feature you'd add to this repository
   - A question about the workshop
4. (Optional) Add the `good first issue` label to your new issue — labels help prioritize work.

## Exercise 3 — Resolve a merge conflict

Your fork contains a branch called `exercise/conflict`. It changes the first line of `CONTRIBUTORS.md` — and so does your `main`. Merging them will produce a **merge conflict**.

1. Make sure you're on `main` and up to date:

   ```bash
   git checkout main
   git pull
   ```

2. Merge the conflict branch:

   ```bash
   git merge exercise/conflict
   ```

   Git stops and marks the conflict inside `CONTRIBUTORS.md`.

3. Open `CONTRIBUTORS.md`. You'll see conflict markers:

   ```
   <<<<<<< HEAD
   ...the version currently on your main...
   =======
   ...the version from exercise/conflict...
   >>>>>>> exercise/conflict
   ```

   - `<<<<<<< HEAD` up to `=======` is **your `main`** version
   - `=======` up to `>>>>>>>` is the **incoming branch** version
   - The markers themselves are not content — delete them and keep the line(s) you actually want (you can even combine both).

4. When the file looks right, mark it resolved and finish the merge:

   ```bash
   git add CONTRIBUTORS.md
   git commit
   git push
   ```

5. Refresh your fork on GitHub — `main` should show the resolved `CONTRIBUTORS.md`, still including your name from Exercise 1.

## Exercise 4 (Bonus) — Sync your fork with the original

Forks don't update themselves. Pull in changes from the original repository:

```bash
git remote add upstream https://github.com/aacayanan/github-workshop.git
git fetch upstream
git merge upstream/main
```

(If your facilitator made changes to the original during the workshop, this is how you get them.)
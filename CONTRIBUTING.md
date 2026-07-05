# Contributing to Nmap-NSE-Script-Collection

Thanks for your interest in contributing! This project collects **defensive, informational** Nmap NSE scripts, and every contribution should stay within that scope.

## Ground Rules

- Scripts must be **defensive/informational** in nature (detection and reporting only — no exploitation, no destructive actions).
- Every script must include a proper NSE header: `description`, `author`, `license`, `categories`.
- Use `categories = {"safe", "discovery"}` or `{"safe", "vuln"}` as appropriate — never `"intrusive"` unless clearly justified and documented.
- Follow the existing folder structure: place new scripts in the matching protocol folder (`HTTP/`, `DNS/`, `SMB/`, `SSL-TLS/`, `DATABASE/`, `FTP/`), or propose a new folder if it's a new protocol.

## How to Contribute

1. **Fork** the repository and clone your fork locally.
2. Create a feature branch:
   ```bash
   git checkout -b feature/my-new-script
   ```
3. Write your script following the style of existing scripts in the same folder (see any `.nse` file for the expected structure: header comment block, `portrule`, `action` function, sample output in comments).
4. Test locally:
   ```bash
   nmap --script-help ./my-new-script.nse
   nmap -p <port> --script ./my-new-script.nse <test-target>
   ```
5. Update the relevant section of `README.md`:
   - Add your script to the category's script list (with description, risk level, what it checks, execution examples, sample output)
   - Add a row to the **Script Reference Summary Table**
   - Update the script counts in the **Statistics** section
6. Commit with a clear, descriptive message:
   ```bash
   git commit -m "Add http-jwt-none-alg-check: detects JWT 'none' algorithm acceptance"
   ```
7. Push and open a **Pull Request** against `main`.

## Pull Request Checklist

Before submitting, confirm:

- [ ] Script runs without errors against a real or lab target
- [ ] Script has a `description`, `author`, `license`, and `categories` field
- [ ] Risk level is accurately assessed (see README's Risk Level Guide)
- [ ] README updated (script list, summary table, statistics)
- [ ] No hardcoded credentials, IPs, or destructive/intrusive actions
- [ ] Code is commented where logic isn't self-explanatory

## Reporting Bugs / False Positives

Open a [GitHub Issue](../../issues) with:
- The script name and Nmap version
- The exact command you ran
- Expected vs. actual output
- Target service/version if relevant (no need to disclose real hostnames/IPs)

## Code of Conduct

Be respectful and constructive. This is a security research/education project — keep discussions professional and focused on improving detection quality.

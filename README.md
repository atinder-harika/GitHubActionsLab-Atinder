Dependent Jobs Workflow
This workflow establishes a strict sequential pipeline where the build, test, and deploy jobs run one after another. It uses the needs keyword to ensure the deploy stage only triggers if the testing stage completes successfully, preventing errors from propagating. This structure enforces a safe order of operations to stop broken code from reaching production.

Multi-Platform Workflow
This script verifies software compatibility by running parallel jobs across Linux, Windows, and macOS environments simultaneously. It utilizes the runs-on keyword to assign specific virtual machines, ensuring the application behaves correctly on different operating systems. The workflow adapts commands for each OS, such as using type for Windows instead of cat, to ensure cross-platform stability.

Key Concepts
The needs key is essential for defining dependencies, turning parallel jobs into a directed graph where specific steps must wait for others to finish. runs-on dictates the target environment, which is critical for testing how your code handles different file paths and system binaries. Although not explicitly used here, env is often paired with these to set global variables and reduce hardcoded values across steps.

Challenges & Resolutions
A primary challenge was handling syntax differences between operating systems, as Windows Command Prompt lacks standard Unix commands like cat or ls. I resolved this by writing specific steps for the windows-job, substituting type and systeminfo to prevent syntax errors. Additionally, using needs solved the issue of jobs running out of order, ensuring the deployment never executes before the tests pass.

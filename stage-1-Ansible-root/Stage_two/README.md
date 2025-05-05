## Stage 2 - Ansible Deployment with Health Checks

This stage focuses on verifying that the YOLO e-commerce app is deployed correctly on the browser.

### Steps:

1. Ensure the app is up from Stage 1 using Ansible.
2. Use `roles/yolo/tasks/verify.yml` to:
   - Check if the frontend is available at `http://localhost:8080`
   - Check if the backend is running at `http://localhost:5000`
3. Run:
   ```bash
   ansible-playbook playbook.yml

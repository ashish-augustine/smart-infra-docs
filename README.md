# smart-infra-docs



How to run
============
1. Create and Activate the Virtual Environment
Run these commands one by one in your VS Code terminal (ensure you are still inside the smart-infra-docs folder):
>
        python3 -m venv venv
        source venv/bin/activate


2. Install All Dependencies Inside the Sandbox
Now that we are safely inside the virtual environment, let's install MkDocs, the Material theme, and the missing extensions:
>
        pip install mkdocs mkdocs-material pymdown-extensions

3. Test the Server Again
Once the installation finishes successfully, run the serve command:
>
        mkdocs serve
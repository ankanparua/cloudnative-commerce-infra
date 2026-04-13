name: "Terraform Pipeline"

on:
  push:
    branches: ["main"]

jobs:
  terraform:
    runs-on: ubuntu-latest

    defaults:
      run:
        working-directory: ./infrastructure

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Terraform
        uses: hashicorp/setup-terraform@v3

      - name: Terraform Init
        run: terraform init -input=false

      - name: Terraform Plan
        run: terraform plan -input=false
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_REGION: ${{ secrets.AWS_REGION }}
          TF_VAR_owner_email: "ankanparua001@gmail.com"

      - name: Terraform Apply
        run: terraform apply -input=false -auto-approve
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_REGION: ${{ secrets.AWS_REGION }}
          TF_VAR_owner_email: "ankanparua001@gmail.com"

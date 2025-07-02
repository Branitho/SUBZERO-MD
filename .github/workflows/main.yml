name: Node.js CI

on:
  schedule:
    - cron: '0 */6 * * *'   # Run every 6 hours (UTC)

jobs:
  build:

    runs-on: ubuntu-latest
    timeout-minutes: 360     # Max 6 hours if needed, but likely finishes sooner

    strategy:
      matrix:
        node-version: [20.x]

    steps:
    - name: Checkout repository
      uses: actions/checkout@v3

    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}

    - name: Install dependencies
      run: npm install

    - name: Start application in background
      run: |
        nohup npm start > app.log 2>&1 &
        sleep 10  # Wait to ensure app starts
        echo "Application started in background"

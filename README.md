- š Hi, Iām @jiumeng6
- š Iām interested in ...
- š± Iām currently learning ...
- šļø Iām looking to collaborate on ...
- š« How to reach me ...

<!---
jiumeng6/jiumeng6 is a āØ special āØ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
name: Fudan Daily

on:
  schedule:
    - cron: '35 00 * * *'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout codes
        uses: actions/checkout@v2
      - name: Setup Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.8'
      - name: Prepare environment
        run: pip install beautifulsoup4 lxml requests
      - name: Run app
        run: python fudanDaily.py
        env:
          USERNAME: ${{ secrets.USERNAME }}
          PASSWORD: ${{ secrets.PASSWORD }}
          PUSH_KEY: ${{ secrets.PUSH_KEY }}

# 🕵 Automated Dorks Search – Guide 

---

## 1. What this program does  
Automated Dorks Search is a little helper that lets you run Google™ searches in bulk and collect the web-page links it finds.  
You type what you’re looking for, press **Search**, and it fills the big white box with clickable web addresses that match your request.  
You can then copy or save those links — and now even **generate a WHOIS-based risk report** to spot suspicious web-stores.

---

## 2. Starting the program
1. **Locate** the folder that contains `main.py` (or use the ready-made installer/exe someone shared with you).  
2. **Double-click `main.py`** – the window titled **“Automated Dorks Search”** opens.

> **Note:** The program needs an **active internet connection** because it contacts Google (and WHOIS servers) in the background.

---

## 3. A quick tour of the window  

### Search tab  
![image](https://github.com/user-attachments/assets/b4c6698d-e035-4645-bd66-18731eb0aa01)



| # | Area | What it’s for |
|---|------|---------------|
| **A** | **Keyword** box | Type your search words here (e.g. *“summer sandals”*). Think of it as the Google search bar. |
| **B** | **Search** button | Starts the search. |
| **C** | **URLs** panel (large white area on the left) | Fills up with the links the program finds. |
| **D** | **What are you looking for?** (checkboxes) | Extra “flavours” of search. Tick one if it matches what you want:<br>• *Products(castaner)* – focuses on typical online-shop pages.<br>• *Detailed_products(universal)* – casts a wider net across many shop-style sites. |
| **E** | **Site Filters** | Fine-tune where Google looks:<br>• *Include sites* – only look inside these sites (type pieces of web addresses, separated by commas).<br>• *Exclude domains* – ignore any site you list here (one per line). |
| **F** | **Hard site exclude** | A stronger “never show” list. Paste domains you **never** want to appear. <br><br>🖼️ *Example:*<br>`shadyshop.com`<br>`weirdbrand.xyz`<br>`fakeoutlet.store` — any link that contains them will be skipped entirely.<br><br>👉 *You can just copy and paste links from domain filter directly:*<br>![alt text](image.png)|
| **G** | **Bottom controls** | **Copy Links** – put every link in your clipboard.<br>**Limit** – how many links you want (1–500; default 20).<br>**Time** – look at pages from *Anytime*, *Past 24 hours*, *Past 7 days*, or *Past 30 days*.<br>**Stop Search** – cancels a running search.<br>**Verbose Logs** – tick to see extra detail in the log box.<br>**Save as CSV / Excel** – store the list as a spreadsheet file.<br>**Generate Report ➜** – create a WHOIS-based risk report from the current URLs. |
| **H** | **Logs** box | A running commentary: what the program is doing, any errors, etc. |

### Reports tab  
![image](https://github.com/user-attachments/assets/ef1a4f2f-63e3-4202-8ef8-ec26541dff9b)

The Reports tab shows a neat table with:

| Column | Meaning |
|--------|---------|
| **URL** | The link you found. |
| **Created** | When the domain was first registered (from WHOIS). |
| **Country** | Registry-reported country. |
| **Age (days)** | How old the domain is. |
| **Risk** | **Low / Medium / High** rating based on age & TLD. |

A **“Save Report as Excel”** button at the top lets you export everything.

### 🛡️ How the “Risk” score is worked out

When you press **Generate Report ➜**, the tool gives each domain a small
numeric score.  Higher = more suspicious.  It then converts that score
into a friendly label (**Low / Medium / High**).

| Adds to the score | Why it matters |
|-------------------|----------------|
| **+1** if the site ends in a “throw-away” TLD such as `.xyz`, `.top`, `.club`, `.shop`, `.store`, `.online`, `.biz`, `.tk`, `.pw`, `.lol`, `.sbs` | These endings are cheap and often favoured by short-lived fake shops. |
| **+2** if the domain’s creation date is hidden or missing | Legitimate stores rarely hide this information. |
| **+2** if the domain is **less than one year old** | New domains haven’t built much reputation yet. |
| **+4** (instead of +2) if the domain is **less than 90 days old** | Very new sites are the riskiest. |

After the points are added up:

| Final score | Shown as |
|-------------|----------|
| 0 – 1 | **Low** |
| 2 – 3 | **Medium** |
| 4 or more | **High** |

### 🔺 When does a site get a **High** risk rating?

Internally the tool adds up a few “suspicion points” for every domain:

| Trigger | Points |
|---------|--------|
| Domain ends with a low-reputation TLD (`.xyz`, `.top`, `.club`, `.shop`, `.store`, `.online`, `.biz`, `.tk`, `.pw`, `.lol`, `.sbs` …) | **+1** |
| WHOIS creation date is missing / hidden | **+2** |
| Domain is **less than 1 year old** | **+2** |
| Domain is **less than 90 days old** | **+4** |

A label is then chosen:

| Total points | Label |
|--------------|-------|
| 0 – 1 | **Low** |
| 2 – 3 | **Medium** |
| 4 +   | **High** |

> **Remember:**  
> The risk rating is a quick indicator, **not** a definitive verdict.  
> Always combine it with your own checks and common sense.


---

## 4. Your first search – step by step

1. **Type a keyword** in the **Keyword** box (Area A) – e.g. **“linen trousers”**.  
2. **Pick a style** *(optional)*:  
   * Tick **Products(castaner)** if you only care about shop pages for that brand.  
   * Tick **Detailed_products(universal)** for a broader product-page hunt.  
3. **Adjust filters** *(optional)*:  
   * **Include sites** – example: `amazon.com, ebay.com` will search only those stores.  
   * **Exclude domains** – example: `facebook.com` will keep Facebook results away.  
4. **Set a limit & time frame** *(optional)* – change **Limit** or **Time**.  
5. Click **Search**. Watch the **Logs** area (H). When it says “✅ Displayed … link(s)” it’s finished.  
6. **Review the links** in the **URLs** panel (C).  
7. **Save or copy** your links:  
   * **Copy Links** – puts them in your clipboard.  
   * **Save as CSV** or **Save as Excel** – saves them as a spreadsheet.

---

## 5. Generating a WHOIS report

1. After you have URLs in the list, press **Generate Report ➜**.  
2. The Logs will show progress (“📝 Generating report…”).  
3. When done, switch to the **Reports** tab (top of the window).  
4. Review the table — suspicious, very new sites are usually flagged **High**.  
5. Press **Save Report as Excel** if you need a file version.

### How risk is calculated

| Condition | Adds to risk |
|-----------|--------------|
| Domain on a “throw-away” TLD (`.xyz`, `.club`, `.shop`, etc.) | +1 |
| WHOIS missing creation date | +2 |
| Domain < 1 year old | +2 |
| Domain < 90 days old | +4 |

Final score → **Risk** column:  
*0-1 = Low* • *2-3 = Medium* • *4+ = High*

---

## 6. Filtering tricks

* **Hide a whole site forever** – list the domain in **Hard site exclude**.  
* **Combine filters** – you can include, exclude *and* hard-exclude at the same time.  
* **See what was filtered** – tick **Verbose Logs** to read every decision.

---

## 7. While the search is running

* Progress messages appear live in **Logs**.  
* Press **Stop Search** to cancel – you’ll see “🛑 Search stopped by user.”  
* Starting a new search automatically clears old results.

---

## 8. Saving your results

| Button | File you get | When to use it |
|--------|--------------|----------------|
| **Save as CSV** | `.csv` text table | Ideal for Excel or Google Sheets. |
| **Save as Excel** | `.xlsx` workbook | A native Excel file with just URLs. |
| **Save Report as Excel** | `.xlsx` workbook | WHOIS report with extra columns (Created, Country, Age, Risk). |

---

## 9. Troubleshooting

| Symptom | What to check |
|---------|---------------|
| **No links appear** | • Is your internet working?<br>• Did you type a keyword? |
| **Red “❌ Error” in logs** | Google or WHOIS server may have blocked a request for a moment. Wait and try again. |
| **WHOIS failed for…** | Some domains hide details or the registry blocks look-ups – the tool skips them automatically. |
| **Program isn’t opening** | Ensure Python is installed, or use the packaged EXE if provided. |

---

## 10. Five-second quick reference

1. **Keyword** → 2. *(optional)* tick a flavour → 3. **Search**  
4. *(optional)* **Generate Report ➜** → 5. **Copy/Save** what you need.  

# Homework 2 - LangChain & Document Parsing

## 前言

* 在前一個作業中，你已經學會使用提示(Prompt)來跟LLM溝通。
* 接下來我們要來看看怎麼蒐集跟處理外部資料。
* 在RAG(Retrieval-Augmented Generation)應用中，如何將外部資料切成適當大小的片段是重要的一個環節。
* 在本次作業中，你將了解使用不同的分割策略(text splitter)來解析文本內容所產生的差異。

## 作業規範

* 請使用 **LangChain**, **PyPDF** 套件完成這次作業。
* 請於 **`student_assignment.py`** 中，實作其中提供的方法
    * `hw02_1(pdf_path)`
    * `hw02_2(pdf_path)`
    * `hw02_3(pdf_path)`

---

### 第一題：使用 CharacterTextSplitter 分割策略讀取 PDF 並解析內容

* **目的**：熟悉如何從外部文件來源取得內容，並透過文本分割工具進行解析。
* **背景**：你手邊有一份範例 PDF 文件 **`OpenSourceLicenses.pdf`**，內容是開源碼授權的基本介紹。
* **任務**：
  1. 使用 **PyPDF** 套件讀取 **`OpenSourceLicenses.pdf`** 的文本內容。
  2. 使用 **CharacterTextSplitter** 將文本以`頁`為單位，分割為多個chunks。
  3. 請回傳最後一個chunk
* **提示**：
  1. 請實作方法 `hw02_1(pdf_path)`，用於完成上述任務。
  2. 可以用 **split_text** 或是 **split_documents** 得到分割後的chunk。
  3. 注意 **CharacterTextSplitter** 的配置參數：
    - 請使用chunk_size=100, chunk_overlap=0
    - separator可以自行決定如何使用
* **預期輸出**：
  - 回傳一個包含檔名、頁數跟內文的物件

---

### 第二題：改用 RecursiveCharacterTextSplitter 分割策略讀取 PDF 並解析內容

* **目的**：探索不同文本分割策略對產生的資料切片的差異。
* **任務**：
  1. 重新設計第一題的文本分割邏輯，改用 **RecursiveCharacterTextSplitter** 將文本分割為段落。
* **提示**：
  - 實作方法 `hw02_2(pdf_path)`。
  - 使用 **split_text** 方法得到分割後的chunk。
  - 注意 **RecursiveCharacterTextSplitter** 的配置參數（請使用chunk_size=1000, chunk_overlap=50）。
* **輸出格式**：
  - 回傳chunk的數量跟跟chunk list中第一個item的內容
    ```
    Number of chunks with RecursiveCharacterTextSplitter: 1803
    CharacterTextSplitter Chunks:
    ['United Nations\nHuman Rights\nReport 2021United Nations\nHuman Rights\nReport 2021Credits ....]
    ```
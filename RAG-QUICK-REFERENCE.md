# RAG Quick Reference Card

## 🚀 Quick Start (3 Commands)

```bash
# 1. Start ChromaDB (leave running)
docker run -p 8000:8000 chromadb/chroma

# 2. Process your files
node process-rag-files.js

# 3. Generate quiz
node FinanceBuddy.js "Your Topic" 10
```

---

## 📁 File Structure

```
FinanceBuddy/
├── RAG_FILES/              ← Drop PDFs/text files here
│   ├── textbook1.pdf
│   ├── guide.txt
│   └── notes.md
├── process-rag-files.js    ← Process files
├── retrieve-context.js     ← Test retrieval
└── FinanceBuddy.js         ← Generate quizzes (modified)
```

---

## 🔧 Commands

### Process Files
```bash
node process-rag-files.js
```
- Processes all files in `RAG_FILES/`
- Skips already-processed files
- Shows progress and summary

### Test Retrieval
```bash
node retrieve-context.js "options trading"
```
- Tests if context is being retrieved
- Shows relevant chunks
- Checks ChromaDB connection

### Generate Quiz
```bash
node FinanceBuddy.js "Options Trading" 10
```
- Automatically retrieves context
- Generates tailored questions
- Falls back to general knowledge if no context

---

## 📝 Supported File Types

- PDF (`.pdf`)
- Text (`.txt`)
- Markdown (`.md`)

---

## ⚙️ Configuration

### Environment Variables (.env)
```bash
GEMINI_API_KEY=your-key-here
CHROMA_URL=http://localhost:8000
CHUNK_SIZE=800
CHUNK_OVERLAP=150
```

---

## 🔍 Troubleshooting

### ChromaDB Not Running
```bash
docker run -p 8000:8000 chromadb/chroma
```

### No Files Found
```bash
# Add files to RAG_FILES/
cp textbook.pdf RAG_FILES/
```

### No Context Retrieved
```bash
# Check if files are processed
node retrieve-context.js "your topic"
```

### Clear Collection
```bash
# Stop ChromaDB, delete data, restart
rm -rf ./chroma_data
docker run -p 8000:8000 chromadb/chroma
```

---

## 📊 What Happens

```
1. Drop file in RAG_FILES/
   ↓
2. Run process-rag-files.js
   ↓
3. File is parsed, chunked, embedded
   ↓
4. Stored in ChromaDB
   ↓
5. Generate quiz
   ↓
6. Context retrieved automatically
   ↓
7. Questions tailored to your textbook!
```

---

## ✅ Success Indicators

### Processing
```
✅ Successfully processed: 2 file(s)
📊 Total chunks created: 98
```

### Quiz Generation
```
✅ Found relevant context (3245 characters)
📖 Using textbook content to tailor questions
```

### Retrieval Test
```
✅ Context retrieved successfully!
Total length: 3245 characters
```

---

## 🎯 Best Practices

1. **Start ChromaDB first** - Always have it running
2. **Process files once** - Already-processed files are skipped
3. **Use specific topics** - Better matching with textbook content
4. **Test retrieval** - Use `retrieve-context.js` to verify
5. **Keep files organized** - Use descriptive filenames

---

## 📚 Example Workflow

```bash
# Day 1: Setup
docker run -p 8000:8000 chromadb/chroma
cp ~/textbooks/*.pdf RAG_FILES/
node process-rag-files.js

# Day 2+: Generate quizzes
node FinanceBuddy.js "Options Trading" 10
node FinanceBuddy.js "Portfolio Management" 5
node FinanceBuddy.js "Risk Analysis" 15
```

---

## 🆘 Quick Help

| Problem | Solution |
|---------|----------|
| ChromaDB error | `docker run -p 8000:8000 chromadb/chroma` |
| No files | Add to `RAG_FILES/` |
| No context | Run `process-rag-files.js` |
| PDF fails | Check if text-based (not scanned) |

---

## 📖 Full Documentation

See `README-RAG.md` for complete guide.

---


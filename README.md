# Public Administrative Procedure Assistant

A Vietnamese virtual assistant that guides citizens through public administrative procedures, such as birth registration, marriage registration and permanent residence registration, and fills in the required declaration forms automatically.

Graduation project, B.Eng. in Information Technology, Ho Chi Minh City University of Technology (HUTECH), 2022.
Thesis title (Vietnamese): *Trợ lý ảo tư vấn, hỗ trợ làm thủ tục dịch vụ công – nền tảng Smart OCR*.

> Vietnamese: Hệ thống tiếp dân thông minh. Tin học hóa quá trình làm dịch vụ công một cách tiện lợi và nhanh chóng.

## Features

- **Vietnamese chatbot** built on a customised ChatterBot engine, with Vietnamese word segmentation (pyvi), stop-word filtering, and semantic matching of paraphrased questions using TF-IDF and a pretrained Vietnamese Word2Vec model.
- **Procedure knowledge base** covering birth registration, re-registration of birth, marriage registration and permanent residence, with the list of required documents for each procedure.
- **Automatic form filling**: generates the declaration form (`.docx`) from information collected in the conversation and stores it in Firebase Cloud Storage.
- **Facebook Messenger integration** through a webhook.
- **Web interface and admin dashboard** (Flask, Flask-Admin, AdminLTE) for managing procedures, documents and conversation history.

The OCR component described in the thesis (extracting personal information from identity documents) is not included in this repository.

## Project structure

```
chatbot/     Chatbot logic: adapters, preprocessing, sentence similarity, training corpus (YAML)
lib/         Customised copy of the ChatterBot library
website/     Flask app: views, auth, admin, form filling (tokhai.py), cloud storage
test/        API tests
main.py      Application entry point
```

## Setup

Requires Python 3.7.

```bash
pip install -r requirements.txt
```

1. **Credentials.** Copy the example files and fill in your own values:
   - `website/secret.example.py` → `website/secret.py` (Facebook Messenger tokens)
   - `website/serviceAccountKey.example.json` → `website/serviceAccountKey.json` (Firebase service account)
2. **Word2Vec model.** The pretrained Vietnamese Word2Vec files are too large for GitHub. Download them from [Google Drive](https://drive.google.com/drive/u/0/folders/1kGTufHpEpJoXwEzl4I5iKH4NzyGcM6bm) and place them in `chatbot/`.
3. **Run.**
   ```bash
   python main.py
   ```

## Team

- Nguyen Trong Nhan
- Nguyen Minh Quan
- Pham Hong Phuc

Supervisor: MSc. Vo Hoang Khang, Faculty of Information Technology, HUTECH.

## References

- Flask tutorial: https://github.com/techwithtim/Flask-Web-App-Tutorial
- Flask admin dashboard: https://github.com/jonalxh/Flask-Admin-Dashboard
- ChatterBot: https://github.com/gunthercox/ChatterBot
- pyvi, Vietnamese NLP toolkit: https://github.com/trungtv/pyvi
- Semantic similarity: https://hal.archives-ouvertes.fr/hal-01683485/document

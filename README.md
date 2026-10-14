# File Agent

Apni files upload karein, kabhi bhi wapis download karein, aur chat bot se un files ke baare mein sawal poochein (Urdu ya English). Sirf aap ke password se khulta hai.

## Kya kya hai
- **Files panel**: drag and drop upload, download, delete (Vercel Blob mein save hoti hain)
- **Chat bot**: tick ki hui files parh kar jawab deta hai. PDF, Word (.docx), Excel, CSV, text aur images samajhta hai
- **File wapis lena**: chat mein likhen "fulan file ka link do", bot download link de dega
- **Login**: ek password, cookie 30 din chalti hai

## Setup (aik martaba)

1. Is folder mein terminal kholen aur chalayen:
   ```
   npm install
   ```
2. `.env.example` ko copy kar ke `.env.local` banayen aur 4 cheezein bharen:
   - `APP_PASSWORD`: aap ka login password
   - `AUTH_SECRET`: koi bhi lamba random text
   - `ANTHROPIC_API_KEY`: https://console.anthropic.com se
   - `BLOB_READ_WRITE_TOKEN`: Vercel project mein Storage, Blob store banane par milta hai
3. Computer par test karne ke liye:
   ```
   npm run dev
   ```
   phir http://localhost:3000 kholen.

## Online (Vercel par) chalana
1. Folder ko GitHub repo mein daalen.
2. vercel.com par "Add New Project" se wo repo import karen.
3. Project ki Settings, Environment Variables mein wohi 4 values daalen.
4. Storage tab mein Blob store banayen aur project se connect karen.
5. Deploy dabayen. Aap ko apna link mil jayega.

## Dhyan dene ki baatein
- Files Blob mein "public" mode mein hain. Un ke link lambe aur random hain (koi andaza nahi laga sakta), lekin jis ke paas link ho wo khol sakta hai. Bohat hassas data ho to link share na karen.
- Chat har sawal par chuni hui files ka text parhta hai, is liye har file se pehle 60,000 characters liye jate hain aur ek waqt mein 8 files tak.
- Scanned PDF (sirf tasweer wale) ka text nahi nikalta; unhein image bana kar upload karen.
- Chat bot ka model `app/api/chat/route.ts` mein `claude-sonnet-5-5` hai, wahan se badal sakte hain.
- Is project ka `npm run build` abhi test nahi hua, pehli martaba chalane par koi chhoti ghalti nikle to bata dein.

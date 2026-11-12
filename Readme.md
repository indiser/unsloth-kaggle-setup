# Unsloth Studio on Kaggle

Notebook: `unsloth-kaggle-setup.ipynb`

Run [Unsloth Studio](https://unsloth.ai) on Kaggle free GPUs. Open UI in browser via Cloudflare tunnel. Search GGUF model in UI, load, chat.

## Requirements

- Kaggle account
- Accelerator: **GPU T4 x2**
- **Internet** on

## Usage

Run cells in order.

| Step | What it does |
|------|--------------|
| 1. Install | Download `https://unsloth.ai/install.sh`, run it. Once per session. |
| 2. Start Studio | Launch `unsloth studio -H 127.0.0.1 -p 8899`. Port 8899 because Kaggle Jupyter uses 8888. Expect `200` at end. |
| 3. Public link | Download `cloudflared`, open tunnel to `127.0.0.1:8899`, print `https://*.trycloudflare.com` URL. |
| 4. First-login password | Print `~/.unsloth/studio/auth/.bootstrap_password`. Paste into **Current password**, then set own password. |

## Notes

- Keep session running. Close it, Studio and link die.
- Tunnel URL changes on each tunnel restart.
- `unsloth` not found: install did not finish. Rerun step 1.
- Model out of memory: pick smaller quant or lower context length in Studio.
- Model downloads go to `/tmp/hf` (`HF_HOME`), not `/kaggle/working`.

## Security

- Anyone with tunnel URL can reach login page.
- Set own password right after first login.
- **Clear step 4 output before saving or sharing notebook.** Bootstrap password sits in cell output.
- Studio can run code. Treat access as full access to session.

# AIID.cz

Statický web aiid.cz (`index.html` + `preview.png`). Běží na webhostingu WEDOS (č. 407111).

## Nasazení

Každá změna ve větvi `main` se automaticky nahraje přes FTP do `/www/` na WEDOSu
(GitHub Actions, `.github/workflows/deploy-wedos.yml`). Ručně: **Actions → Nasazení aiid.cz na WEDOS → Run workflow**.

Potřebné **Secrets** (Settings → Secrets and variables → Actions):

- `FTP_SERVER`: `407111.w11.wedos.net`
- `FTP_USERNAME`: `w407111`
- `FTP_PASSWORD`: heslo k hlavnímu FTP účtu

Pokud FTP spojení selže na TLS, změň ve workflow `protocol: ftps` na `protocol: ftp`.

## Co se na serveru nesmí smazat

- `/www/.htaccess` – WEDOS podle něj přiřazuje domény a subdomény ke složkám.
- `/www/subdom/` – weby účastníků kurzu (`jmeno.aiid.cz`), každý má vlastní FTP účet omezený na svou složku.

Workflow nahrává jen soubory webu a nic jiného na serveru nemaže.
`index_ok.html` a `index_pills.html` jsou starší varianty a na server se nenahrávají.

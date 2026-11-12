# FallenLight

Ambilight pentru banda LED **Robobloq** (controller USB `1a86:fe07`) pe Windows 10/11.
Banda preia culorile de pe marginile ecranului, fără DX Light / SyncLight și fără să încetinească Windows-ul.

## Descărcare

Ultima versiune: **[Releases → Latest](../../releases/latest)** → descarcă `FallenLight-vX.Y.zip`, dezarhivează și pornește `FallenLight.exe`.

- Nu trebuie instalat nimic (.NET e inclus).
- La prima pornire Windows poate afișa „Windows a protejat PC-ul” (aplicația nu e semnată digital):
  **Mai multe informații → Rulează oricum**.
- Închide DX Light / SyncLight și OpenRGB înainte, altfel își suprascriu culorile.

## Actualizări

Din meniul din tray sau din Setări: **Verifică actualizări**. Versiunea nouă se descarcă,
se verifică și se instalează singură, apoi aplicația repornește (setările se păstrează).

## Ce face

- Captură eficientă (DXGI Desktop Duplication, micșorare pe placa video) — ~1–3% dintr-un nucleu.
- Suport HDR, corecție gamma, prag de negru, netezire, saturație.
- Configurare sens bandă + buton de test pentru laturi.
- Stinge banda la shutdown, sleep și când monitorul intră în standby.

© 2026 Fallen

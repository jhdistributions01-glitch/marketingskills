# Ads Manager UI traps (Spanish UI, 2026)

Last verified: 2026-11-03 in a live account (Equipos360, Colombia). Review by: 2027-01-15.
These are defaults and behaviors of the Ads Manager editor that silently change what you publish.
Check every item before clicking Publicar. UI labels are the Spanish ones.

## Creative and ad level

1. **9:16 video fails Instagram Feed.** In a "Una sola imagen o video" ad, a 9:16-only video gives
   the error "El video que subiste solo se puede publicar en Instagram Stories... relación de
   aspecto de 4:5 a 1,91:1". Fix: add a **4:5 version of the same video inside the same ad** (an ad
   accepts up to 10 media; Meta picks per placement). Make the 4:5 with a blurred background
   instead of cropping, so no on-screen text is cut:
   ```bash
   ffmpeg -i in_9x16.mp4 -filter_complex "[0:v]scale=1080:1350:force_original_aspect_ratio=increase,crop=1080:1350,boxblur=30:5,eq=brightness=-0.15[bg];[0:v]scale=-2:1350[fg];[bg][fg]overlay=(W-w)/2:0,format=yuv420p" -c:v libx264 -crf 24 -c:a aac -movflags +faststart out_4x5.mp4
   ```
2. **"Productos" (catalog) comes ON** in new ads ("Configuración del contenido: Productos Activado,
   Catálogo predeterminado"). Turn it off for resellers or when catalog items show third-party brands.
3. **"Anuncios multianunciante" comes checked.** It can resize/crop the content; uncheck it when
   on-screen text matters.
4. **Advantage+ creative enhancements**: review "Retoques de video", "Agregar detalles al diseño",
   "Agregar efectos de video" (all OFF for videos with burned-in text), "Mejoras en el texto"
   (rewrites/moves copy). From the new Commercial Terms (effective 2026-11-20 per third-party
   reports) the advertiser is responsible for AI-generated content: keep text-writing and
   product-altering enhancements OFF unless reviewed; leave crop/expand/brightness if wanted.
5. **"Generación de contenido Advantage+" (Meta AI images/videos)**: nothing is selected by default
   but the step shows generated assets with your brand and phone number. Keep "0 seleccionados".
6. **Duplicating an ad copies its message template**, so its predefined message stays the old
   one. Change the template per ad (Conversaciones > Plantillas guardadas) or the CRM cannot tell
   ads apart.

## Ad set level

7. **Duplicate dialog pre-checks recommendations**: "Llegar a las personas interesadas en tus
   lugares" and "Usa el objetivo de rendimiento de compras a través de mensajes". Uncheck both
   unless intended. A second step also shows "Llegar a más personas con probabilidades de
   responder a mis anuncios" ON.
8. **"Llegar a más personas con probabilidades de responder a tus anuncios"** (inside Lugares) comes
   ON: it shows ads outside the selected places. Turn off for local stores.
9. **New city locations default to +40 km radius.** Set nearby towns to "Solo ciudad actual" and the
   main pin to the minimum 17 km if the store is local.
10. **Ad set budget with "Compartir hasta un 20% de tu presupuesto con otros conjuntos"** comes ON.
    Turn it off when ad sets have different jobs (local vs remarketing); a confirmation pops up.
11. **Switching Advantage+ audience to original audience** ("Limitar aún más tu público" >
    "Cambiar configuración") turns inherited "suggested" interests into restrictive targeting. Clear
    "Segmentación detallada" when the custom audience is the targeting (remarketing).
12. **New ad sets (or ad sets whose locations change) may show "Cuenta de WhatsApp Business
    obligatoria (#2923012)"**. See click-to-whatsapp-smb.md section 5 before acting. Do NOT
    migrate an API number from the phone.
13. **Campaign default budget** on a brand-new campaign can be large (seen COP 339.500/day). Always
    set budget level and amount explicitly before moving on.

## Publishing

14. **"Revisar y publicar (N)" includes every draft in the account**, old ones included (old
    catalog remarketing, old ads). Uncheck rows you do not want; rename abandoned drafts with a
    "ZZ ... NO PUBLICAR" prefix so they are obvious.
15. **The review dialog can re-check rows** after toggling tabs or "Intentar publicar elementos con
    errores". Re-read the "Conjuntos X de N / Anuncios X de N" counters right before clicking
    Publicar.
16. **Errors in the review dialog can be stale or non-blocking.** The 4:5 Instagram error stayed
    listed after the fix and the ads still published; "Intentar publicar elementos con errores"
    published ads with the #2923012 notice and Meta accepted them for review. Verify the real status
    in the Ads table afterwards (Procesando / En revisión / Activo / Rechazado).
17. **Escape key closes the editor** and pops "¿Publicar borradores?". Click "Cerrar" (not Publicar);
    drafts are kept.
18. **The left tree reorders** after edits/duplicates. Confirm the breadcrumb (campaign > ad set >
    ad) before editing; clicking by position can open an ad in another ad set.

## Browser notes

- Brave's ad blocker breaks parts of Ads Manager (it shows a "Desactivar bloqueador de anuncios"
  notice). Use Chrome or disable shields for facebook.com.
- With the location map visible the page can freeze screenshots/automation; collapse the map
  ("Toggle map") when editing locations.

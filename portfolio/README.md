# التحكم فإعلانات التطبيقات الخمسة

النسخة الأولى غتخرج والإعلانات مطفّية عند جميع المستخدمين. Real IDs غير من بعد خروج التطبيق واعتـماد Yandex للحساب والتطبيق. ملفات JSON هنا عمومية: ممنوع كلمات السر، tokens، بيانات البنك أو مفاتيح خاصة.

| التطبيق | ملف التحكم | تعديل مباشر |
|---|---|---|
| Словодень: поиск слов | [wordtrail.json](v1/wordtrail.json) | [Edit](https://github.com/soufianelh2022/ads/edit/main/portfolio/v1/wordtrail.json) |
| СменаРитм: график смен | [shiftledger.json](v1/shiftledger.json) | [Edit](https://github.com/soufianelh2022/ads/edit/main/portfolio/v1/shiftledger.json) |
| ЛистPDF: документы и фото | [docready.json](v1/docready.json) | [Edit](https://github.com/soufianelh2022/ads/edit/main/portfolio/v1/docready.json) |
| ПлатёжКруг: календарь оплат | [billcalendar.json](v1/billcalendar.json) | [Edit](https://github.com/soufianelh2022/ads/edit/main/portfolio/v1/billcalendar.json) |
| ДомСчёт: показания счётчиков | [meterbook.json](v1/meterbook.json) | [Edit](https://github.com/soufianelh2022/ads/edit/main/portfolio/v1/meterbook.json) |

## من بعد Live

1. كمّل Yandex onboarding وتحقق الملكية/moderation. استعمل ID ديال النوع الصحيح `R-M-…-…`، ماشي demo ID.
2. حدّث App Privacy والسياسة إذا تبدل جمع البيانات. placements معلنة فـApp Review notes؛ ما كاين لا reviewer detection ولا إخفاء أثناء المراجعة.
3. زيد `revision` برقم واحد فكل تغيير. خليه دائماً كيزيد.
4. بدّل `unitID` ثم `enabled` ديال placement المختار إلى `true`، و`enabled` الرئيسي إلى `true`. المستخدم خاصو حتى هو يختار الإعلانات فالإعدادات.
5. `minimumSecondsBetweenFullscreen` بين 180 و3600 ثانية، و`maximumFullscreenPerDay` بين 0 و6. اقتراح: 180 ثانية و4 فالنهار. Rewarded وInterstitial كيتقاسمو نفس السقف.
6. `validUntil: null` كيخلي الملف صالح بلا تاريخ نهاية؛ تقدر تحدد UTC ISO-8601 حتى لعام واحد. التطبيق كيوقف الإعلانات إذا فشل التحديث، الملف غير صالح أو انتهى؛ آخر تحديث صالح كيتقادم بعد 15 دقيقة. التغييرات ماشي لحظية.
7. للإيقاف: زيد revision وبدّل enabled الرئيسي إلى false ثم Commit. تأكد من الرابط Raw.

GitHub كيتحكم غير فالـIDs، الأماكن الموجودة أصلاً، التفعيل والسقف. ما يقدرش يزيد feature، ينزّل code أو يجاوز اختيار المستخدم. ما كاين حتى رابط بين بيانات الوثائق/المدفوعات/الأجور/العدادات وطلبات الإعلانات.

## Placements

- WordTrail: `library` banner، `extraHint` rewarded اختياري، `betweenRounds` interstitial بعد إكمال الجولة والضغط Done إذا كان واجد.
- ShiftLedger: `reports` banner.
- DocReady: `library` banner.
- BillCalendar وMeterBook: `history` banner.

الدعم والسياسات: `portfolio/<appID>/index.html`. سورس التطبيقات ومفاتيح التوقيع ما كيتنشروش هنا.

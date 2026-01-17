# Kanıta Dayalı AB Makine Kullanma Kılavuzu Şablonu (CE)

**Canlı dokümanlar:** https://saimgulay.github.io/ab-makine-kullanma-kilavuzu-sablonu/

## DOCX sürümü
- Konum: docs/MANUAL_TEMPLATE_TR.docx
- Kaynak (tek doğruluk kaynağı): docs/MANUAL_TEMPLATE_TR.md

### Geliştirici notu (MD ve DOCX senkronu)
Markdown şablonu tek doğruluk kaynağıdır. MD dosyasında değişiklik yaptıysanız, DOCX dosyasını da mutlaka yeniden üretmelisiniz.

Önerilen üretim (en iyi sadakat):
- Pandoc varsa:
  - pandoc -f gfm -t docx -o docs/MANUAL_TEMPLATE_TR.docx docs/MANUAL_TEMPLATE_TR.md

Yedek üretim (Pandoc yoksa):
- Python + python-docx kullanın (bu repoda kullanılan dönüştürme yaklaşımını commit geçmişinde görebilirsiniz).

Bu depo, endüstriyel makineler için **kanıta dayalı** bir kullanma kılavuzu (instruction handbook) şablonu ve izlenebilirlik/evidence çerçevesi sağlar:
- AB Makine Direktifi **2006/42/EC** Ek I §1.7.4 (Instructions) ve AB Makine Tüzüğü **(EU) 2023/1230** odaklı bir kılavuz iskeleti
- “Uygunluk matrisi”: mevzuat gerekliliği → kılavuz bölümü eşlemesi
- “Kanıt paketi (evidence pack)” klasör yapısı + SHA-256 hash listesi
- Uygunluk raporu ve kanıt indeks şablonları

## Kapsam
- Hedef: endüstriyel makine kullanma kılavuzları (kullanıcı/operatör + gerekli ise bakım/servis bilgileri)
- Format: Markdown (PDF/Word/Pages’e kolay aktarılır; docs-as-code iş akışlarına uygundur)

## Birincil hukuk referansları
- 2006/42/EC (Makine Direktifi) Ek I §1.7.4 “Instructions”
- (EU) 2023/1230 (Makine Tüzüğü) — 2006/42/EC’nin yerini alır; genel uygulama tarihi **20 Ocak 2027** (bazı hükümler daha erken)

> Not: Uygulanabilir gereklilikler makine sınıfına, amaçlanan kullanıcı profiline ve Üye Devlet dil/dağıtım kurallarına göre değişebilir.
> Bu repo bir şablon ve izlenebilirlik çerçevesidir; **hukukî görüş değildir.**

## Hızlı kullanım
1. docs/MANUAL_TEMPLATE_TR.md dosyasını kopyalayıp ürününüze göre isimlendirin.
2. Token’ları (bkz. docs/STYLE_GUIDE.md) eksiksiz doldurun.
3. Kanıt paketi oluşturun:
   - macOS/Linux: scripts/new_evidence_pack.sh "urun_slug"
   - Windows PowerShell: scripts/new_evidence_pack.ps1 -ProductSlug "urun_slug"
4. Kanıt paketini doldurun (risk değerlendirmesi özeti, test logları, çizimler, etiket envanteri, çeviri artefaktları).
5. docs/COMPLIANCE_MATRIX.md dosyasını doldurun ve docs/COMPLIANCE_REPORT_TEMPLATE.md ile raporlayın.

## Depo kuralları
- Her yayımlanan kılavuz revizyonu için:
  - evidence/_packs/<timestamp>_<slug>/ altında karşılık gelen kanıt paketi
  - scripts/make_hashes.py ile üretilmiş SHA-256 listesi
  - Kanıt yolları + hash’leri referanslayan uygunluk raporu önerilir

## Lisans
- Dokümantasyon şablonları: CC BY 4.0 (bkz. LICENSE ve LICENSES/LICENSE-CC-BY-4.0.md)
- Script’ler: MIT (bkz. LICENSES/LICENSE-MIT.md)
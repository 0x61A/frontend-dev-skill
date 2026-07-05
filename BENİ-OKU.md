# FrontendDev — Türkçe Kullanım Kılavuzu

Genel yapay zeka frontend görünümünü kıran, her seferinde **benzersiz** ve **SEO'su tam** siteler üreten skill. Diğer tasarım skilllerinden bağımsız çalışır, onları değiştirmez.

## Ne yapar?

1. **Tasarım DNA'sı** — Her proje için sıfırdan: isimlendirilmiş renk paleti (4-6 hex), font çifti, layout iskeleti (ASCII wireframe ile), tek imza öğesi, motion seviyesi. Aynı brief'i iki kez versen iki farklı tasarım çıkar.
2. **Yasaklı desen kontrolü** — Bilinen "AI işi" kalıpları (mor gradient hero, cream+terracotta, Inter başlık, emoji'li 3'lü kart grid'i, "Elevate your..." kopyası, her şeye fade-in-up...) 36 maddelik katalogda; DNA bu listeye takılırsa o eksen yeniden üretilir. Ayrıca **kalıcı design-log**: her geçen build kaydedilir, yeni DNA eski build'lerle 2+ eksende (iskelet, hero kompozisyonu, palet ailesi) çakışırsa o eksen yeniden atılır — oturumlar arası benzerlik de yakalanır.
3. **Referans site analizi** — URL at ("şu siteye benzet"), skill görsel (screenshot/Chrome) + kod (WebFetch ile renk/font/spacing çıkarımı) analizi yapar, **Reference Design Brief** yazar. Asla kopyalamaz — ilke çıkarır, üstüne bilinçli fark ekler.
4. **Komponent çek + dönüştür** — 21st.dev, shadcn/ui, Aceternity, Magic UI vb. 16 kaynaktan canlı kod çeker; ama her renk/font/radius/shadow projenin DNA token'larıyla yeniden yazılmadan asla commit edilmez.
5. **Tam SEO** — Keyword araştırması (Semrush MCP bağlıysa gerçek veri, değilse WebSearch) sayfa mimarisinden ÖNCE yapılır; semantic HTML, meta/OG, JSON-LD schema, sitemap, robots.txt, Core Web Vitals bütçeleri (LCP<2.5s, CLS<0.1, INP<200ms) zorunlu.
6. **Screenshot self-critique** — Build bitince önce doğrulama reçetesi (375px taşma kontrolü + computed-value kontrast), sonra screenshot alınır, 10 maddelik "bu AI işi mi?" testinden geçirilir; geçemezse ilgili eksen revize edilir. Mobil + desktop + (varsa) dark mode. Geçen build design-log'a işlenir.
7. **Çok sayfalı site + Türkçe mikrocopy** — Çok sayfada "kardeş sayfa" kuralları (tek token kaynağı, sayfa başına iskelet varyasyonu); Türkçe projelerde sektöre özgü CTA/form/hata metni bankası.

## Nasıl tetiklenir?

- `/frontend-dev` yazarak, veya doğal cümleyle:
- "X için benzersiz bir landing page yap"
- "Bu siteye benzet: https://..." / "şu sitenin tasarımını referans al"
- "AI işi gibi durmayan, SEO uyumlu site istiyorum"
- "21st.dev'den hero çek, projeye uyarla"

## Örnek akışlar

**Sıfırdan site:**
> "Bir kahve kavurma atölyesi için landing page — benzersiz olsun, SEO'lu"
→ Brief soruları (eksikse) → DNA üretimi → keyword araştırması → stack seçimi (muhtemelen Astro/plain HTML) → build → screenshot testi.

**Referanslı:**
> "https://ornek-site.com tarzında ama bize özgü bir portfolyo"
→ Referans analizi (görsel+kod) → Reference Design Brief (onayına sunulur) → DNA (brief'ten + bilinçli sapma) → build.

**Komponent hızlandırmalı:**
> "Pricing bölümü lazım, hazırdan başla"
→ Kaynak önerisi (2-3 aday) → canlı kod çekimi → DNA'ya göre tam dönüşüm → a11y denetimi.

## Dosya haritası

| Dosya | İçerik |
|---|---|
| `SKILL.md` | 6 fazlı workflow + sert kurallar + routing |
| `references/design-dna.md` | DNA üretim süreci + DNA kartı formatı |
| `references/anti-generic.md` | 10 maddelik AI-tell testi + critique döngüsü + kalite tabanı |
| `references/reference-analysis.md` | Referans site analizi + brief şablonu |
| `references/component-sourcing.md` | Çek + dönüştür kuralları + görsel kaynak rehberi (Unsplash/Pexels/Openverse + treatment reçeteleri) |
| `references/multi-page.md` | Çok sayfalı site: tek DNA, kardeş sayfalar |
| `references/seo-full.md` | Keyword → mimari → on-page → schema → CWV |
| `references/stack-selection.md` | Stack karar ağacı |
| `data/banned-patterns.md` | 36 yasaklı desen (HARD + CONDITIONAL) + geçme kriterleri |
| `data/style-axes.csv` | 72 satırlık DNA stil matrisi (hero_composition ekseni dahil) |
| `data/font-pairings.csv` | 58 karakterli font çifti (Inter/Roboto display yasak; Türkçe diyakritik notu dahil) |
| `data/component-sources.csv` | 20 canlı komponent kaynağı + dönüşüm notları |
| `data/microcopy-tr.md` | Türkçe mikrocopy bankası (CTA/form/hata/ton) |
| `design-log.md` | Kalıcı build kaydı — oturumlar arası benzerlik kontrolü |

## Notlar

- Kullanıcının açık isteği her zaman kazanır — brief "mor gradient istiyorum" diyorsa yasak listesi devre dışı.
- Erişilebilirlik, benzersizlikle çatışırsa her zaman kazanır.
- Admin panel / dahili araç gibi salt işlevsel UI'larda benzersizlik makinesi çalışmaz; sadece kalite tabanı + gerekli SEO uygulanır.
- Skill güncellemek için: bu klasördeki dosyaları düzenle, yeni oturumda geçerli olur.

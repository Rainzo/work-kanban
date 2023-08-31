# Source definition query

Created: September 29, 2022 2:41 PM
Last edited: September 29, 2022 2:42 PM

```sql
--source
    case when "source_name" like '%direct%' then 'Direct traffic'
    when "source_name" like '%mobile-app%' then 'mobile-app'
    when "source_name" like 'facebook.com' then 'facebook.com'
    when "source_name" like '%google.%' and "campaign" = '--empty--' then 'Google Organic'
    when "source_name" like '%bing.com%' and "campaign" = '--empty--' then 'Bing Organic'
    when "source_name" like '%seznam.cz%' and "campaign" = '--empty--' then 'seznam.cz'
  /*
    --case when "source_name" like '%email%' then 'Email'
    --when "source_name" like '%yahoo.%' and "campaign" = '--empty--' then 'yahoo.'
    --when "source_name" like '%ecosia.%' and "campaign" = '--empty--' then 'ecosia.'
    --when "source_name" like '%seznam.sk%' and "campaign" = '--empty--' then 'seznam.sk'
    --when "source_name" like '%centrum.%' and "campaign" = '--empty--' then 'centrum.'
    --when "source_name" like '%duckduckgo.%' and "campaign" = '--empty--' then 'duckduckgo'
    --when "campaign" like '%CSS%' or "source_name" like '%glami_css%' then 'Google Ads CSS'
    when "source_name" like '%fb_fb_page_saty%' then 'fb_fb_page_saty.'
    when "source_name" like '%fb_fb_page_svet_kabelek%' then 'fb_fb_page_svet_kabelek'
    when "source_name" like '%fb_fb_page_vasen_pro_boty%' then 'fb_fb_page_vasen_pro_boty'
    when "source_name" like '%fb_fb_page%' then 'fb_fb_page'
    when "source_name" like '%fb_fb_page_krasna_pri_sportu%' then 'fb_fb_page_krasna_pri_sportu'
    when "source_name" like '%fb_fb_page_vikend%' then 'fb_fb_page_vikend'
    when "source_name" like '%fb_fb_page_premium%' then 'fb_fb_page_premium'
    when "source_name" like '%fb_fbpage_lumea_rochiilor%' then 'fb_fbpage_lumea_rochiilor'
    when "source_name" like '%fb_fbpage%' then 'fb_fbpage'
    when "source_name" like '%fb_fb_pages%' then 'fb_fb_pages'
    when "source_name" like '%fb_fb_page_vasen_pre_topanky%' then 'fb_fb_page_vasen_pre_topanky'
    when "source_name" like '%fb_fb_page_svet_nadhernych_siat%' then 'fb_fb_page_svet_nadhernych_siat'
    when "source_name" like '%fb_fb_page_sk_panske_outfity%' then 'fb_fb_page_sk_panske_outfity'
    when "source_name" like '%fb_fb_page_lubim_reducerile%' then 'fb_fb_page_lubim_reducerile'
    when "source_name" like '%fb_fb_page_krasna_pri_sporte%' then 'fb_fb_page_krasna_pri_sporte'
    when "source_name" like '%fb_fb_page_kizelny_svet_kabeliek%' then 'fb_fb_page_kizelny_svet_kabeliek'
    when "source_name" like '%fb_fb_page_cipo_m%' then 'fb_fb_page_cipo_m'
    when "source_name" like '%fb_fb_page_akciok_divtermk%' then 'fb_fb_page_akciok_divtermk'
    when "source_name" like '%fb_fb_page_Iubim_gentile_si_pantofii%' then 'fb_fb_page_Iubim_gentile_si_pantofii'
  */
    when "campaign" like '%Stileo.it REF%' or "campaign" like '%Stileo.it+REF%' then 'fb_fb_pages (Old boost campaigns)'
    when ("source_name" like '%fb_fb_page%' or "source_name" like '%fb_page%') and "campaign" not like '%Stileo.it REF%' then 'Facebook Pages'
    when "campaign" like '%SCH%' and "source_name" like '%google_cpc%' then 'thp_google_search'
    when ("campaign" like '%DNB%' or "campaign" like '%RMKT%') and "source_name" like '%google_cpc%' then 'thp_google_display'
    when "campaign" like '%GCO%' and "source_name" like '%google_cpc%' then 'thp_google_checkout'
    --facebook:
    when ("campaign" like '%RMKT%' or "campaign" like '%converters%' or "campaign" like '%DPA%' or "campaign" like '%RH DPA GLAMIDAYS AUTO - CROSS SELL%' 
          or "campaign" like '%RH DPA GLAMIDAYS AUTO - AUD PURCHASERS%' or "campaign" like '%RH DPA GLAMIDAYS AUTO - CONV%') 
          and "campaign" not like '%ATC%' and "source_name" like '%facebook_cpc%' then 'Facebook Remarketing'
    when ("campaign" like '%Prosp%' or "campaign" like '%PROSP%' or "campaign" like '%RH DPA GLAMIDAYS AUTO - W FASHION%' 
          or "campaign" like '%RH DPA GLAMIDAYS AUTO - M FASHION%' or "campaign" like '%PDPA%') 
          and "campaign" not like '%ATC%' and "source_name" like '%facebook_cpc%' then 'Facebook Remarketing'
    when "campaign" not like '%ATC%' and "campaign" like '%DPA%' and "source_name" like '%facebook_cpc%' then 'Facebook DPA Campaigns - Prosp. & Rmkt'
    when "campaign" like '%ATC%' and "source_name" like '%facebook_cpc%' then 'Facebook ATC - Glami Audiences'
    when "campaign" not like '%ATC%' and "channel" not like '%Facebook Ads%' and "source_name" = 'facebook_cpc' then 'Facebook Static Banners'
    --sklik:
    when ("campaign" like '%Glami%' or "campaign" like '%Domodi%') and "source_name" = 'sklik_cpc' then 'Sklik brand search'
    when ("campaign" like '%SCH%' or "campaign" like '%DSA%' or "campaign" like '%YD%') and "source_name" = 'sklik_cpc' then 'Sklik search'
    when ("campaign" like '%DNB%' or "campaign" like '%prospecting%') and "source_name" = 'sklik_cpc' then 'Sklik display'
    when ("campaign" like '%RMKT%' or "campaign" like '%converters%') and "source_name" = 'sklik_cpc' then 'Sklik remarketing'
    --bing:
    when ("campaign" like '%Glami%' and "campaign" like '%SCH%' or "campaign" like '%S0%' and "campaign" like '%stileo brand%') and "source_name" like '%bing_cpc%' then 'Bing Ads Brand Search'
    when ("campaign" like '%SCH%' or "campaign" like '%YD%' or "campaign" like '%S0%') and "campaign" not like '%Glami%' and "campaign" not like '%stileo brand%' and "source_name" like '%bing_cpc%' then 'Bing Ads Search'
    when ("campaign" like '%DNB%' or "campaign" like '%PROSP') and "source_name" like '%bing_cpc%' then 'Bing Ads Prospecting'
    when ("campaign" like '%RMKT%' or "campaign" like '%converters%') and "source_name" like '%bing_cpc%' then 'Bing Ads Prospecting'
    --pinterest & tiktok:
    when ("campaign" like '%PROSP%' or "campaign" like '%prospecting%') and "source_name" like '%pinterest_cpc%' then 'Pinterest Prospecting'
    when ("campaign" like '%RMKT%' or "campaign" like '%converters%') and "source_name" like '%pinterest_cpc%' then 'Pinterest Remarketing'
    when ("campaign" like '%PROSP%' or "campaign" like '%prospecting%') and "source_name" like '%tiktok_cpc%' then 'TikTok Prospecting'
    when ("campaign" like '%RMKT%' or "campaign" like '%converters%') and "source_name" like '%tiktok_cpc%' then 'TikTok Remarketing'
    --the rest:
    when "source_name" like '%criteo_cpc%' then 'criteo_cpc'
    when "source_name" like '%dbm_cpm%' then 'dbm_cpm'
    when "source_name" like '%seznam_banner%' then 'Seznam banner'
    when "source_name" like '%taboola_cpc%' or "source_name" like '%Taboola_cpc%' then 'Taboola_cpc'
    when "source_name" like '%strossle_cpc%' then 'strossle_cpc'
    when "source_name" like '%mgid.com_cpc%' then 'mgid.com_cpc'
    --when "source_name" like '%dbm_cpm%' then 'Doubleclick Prospecting'
    when "source_name" like '%ig_ig_page%' or "source_name" like 'instagram.com' then 'Instagram Organic'
    when "source_name" like '%FBShopping_Social%' then 'FBShopping_Social'
    when "source_name" like '%IGShopping_Social%' then 'IGShopping_Social'
    when "source_name" like '%zbozi.cz_cpc%' then 'zbozi.cz_cpc'
    when "source_name" like '%aiqua_%' then 'WebPush'
    else 'other' end as "Source",
```
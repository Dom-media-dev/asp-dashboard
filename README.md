# ASP — Dashboard client (SaaS Acquisition Scale Partner)

En ligne sur https://asp-saas.com (espace agence : https://asp-saas.com#agence).
Page statique servie par le Worker Cloudflare `royal-pine-d2ad`, déployée automatiquement à chaque push sur `main`.
Toutes les données sont lues en temps réel dans Supabase (projet `camezagvyeavzpyvofvk`).

## Ajouter un nouveau client
1. Ajouter une ligne dans `public.clients` : nom, secteur, commission, setup, mensuel, IDs Meta et GoHighLevel (location, calendrier, pipeline).
2. Optionnel : `config.pillars` (contenu des 5 piliers adapté au secteur) et `config.sale_label` (ex. « Véhicules vendus »).
3. Créer son compte (Supabase Auth) puis une ligne `public.dashboard_users` (role = 'client', client = nom exact).
4. Les tâches quotidiennes alimentent automatiquement ses données (Meta → dashboard_metrics, GHL → RDV / ventes / WhatsApp).

## Tables
- clients : configuration de chaque client
- dashboard_metrics : chiffres mensuels (Meta + GHL)
- whatsapp_agent_metrics : relevés de l'agent WhatsApp
- setter_daily_metrics / setter_leads / setter_changes / setter_prompt_versions : mémoire chiffrée du setter IA
- automation_logs, competitive_intelligence, connected_sources, dashboard_users

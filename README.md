# Simple-Crypto-App
A simple and responsive mobile-style application built with Ionic + Vue + TypeScript to display live cryptocurrency prices.
The app fetches real-time data from a public crypto API, displays it in a clean list layout, and includes a refresh button to update prices instantly.

Features

Live cryptocurrency price fetch using external API
Refresh button to reload latest price data
Mobile-friendly UI designed with Ionic components
Clean green-black theme for modern look
Built with Vue 3 + TypeScript + Ionic Framework

Project Structure
src/
│── components/
│── router/
│── services/
│    └── APIService.ts      → API handler for fetching crypto data
│── views/
│    ├── Tab1Page.vue       → Crypto List Page (main page)
│    ├── Tab2Page.vue
│    ├── Tab3Page.vue
│    └── TabsPage.vue
│── App.vue
│── main.ts

Installation

Clone repository:
git clone https://github.com/username/your-repo.git
cd your-repo


Install dependencies:
npm install

Run the app:
ionic serve

API Used
Cryptocurrency data is fetched from:
https://api.coincap.io/v2/assets

How It Works
APIService.ts handles API requests

Tab1Page.vue calls APIService and displays crypto list

Clicking Refresh runs the fetch function again

Data is shown in a table-like list with gradients

Future Improvements
Add search bar
Add detail page for each coin
Add dark/light mode toggle
Add paging or limit options

Tech Stack
Ionic Framework
Vue 3
TypeScript
CoinCap API

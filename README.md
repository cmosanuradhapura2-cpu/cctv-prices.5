<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>C-MOS CCTV Price List & Inventory System</title>

  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>

  <!-- Google Fonts: Inter & Noto Sans Sinhala -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Noto+Sans+Sinhala:wght@400;500;600;700&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          colors: {
            brand: {
              50: '#eef2ff',
              100: '#e0e7ff',
              500: '#6366f1',
              600: '#4f46e5',
              700: '#4338ca',
              900: '#312e81'
            }
          },
          fontFamily: {
            sans: ['Inter', 'Noto Sans Sinhala', 'sans-serif'],
          }
        }
      }
    }
  </script>

  <style>
    body {
      font-family: 'Inter', 'Noto Sans Sinhala', sans-serif;
      background-color: #0f172a;
      color: #f8fafc;
    }
    
    select option {
      background-color: #0f172a !important;
      color: #f8fafc !important;
      padding: 10px !important;
    }

    .custom-scrollbar::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    .custom-scrollbar::-webkit-scrollbar-track {
      background: #1e293b;
    }
    .custom-scrollbar::-webkit-scrollbar-thumb {
      background: #475569;
      border-radius: 3px;
    }

    @media print {
      .no-print {
        display: none !important;
      }
      body {
        background-color: #ffffff !important;
        color: #000000 !important;
      }
      .print-table {
        width: 100% !important;
        border-collapse: collapse !important;
      }
      .print-table th, .print-table td {
        border: 1px solid #cbd5e1 !important;
        padding: 8px !important;
        color: #000000 !important;
      }
    }
  </style>
</head>
<body class="min-h-screen flex flex-col justify-between custom-scrollbar bg-slate-900 text-slate-100">

  <!-- HEADER / NAVBAR -->
  <header class="sticky top-0 z-30 bg-slate-800/90 backdrop-blur-md border-b border-slate-700 shadow-lg no-print">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3.5 flex flex-col md:flex-row items-center justify-between gap-4">
      
      <!-- Brand & Title -->
      <div class="flex items-center justify-between w-full md:w-auto">
        <div class="flex items-center space-x-3">
          <div class="p-2.5 bg-gradient-to-tr from-indigo-600 to-violet-500 rounded-xl shadow-md text-white">
            <i data-lucide="video" class="w-6 h-6"></i>
          </div>
          <div>
            <h1 class="text-xl font-bold tracking-tight text-white flex items-center gap-2">
              C-MOS COMPUTERS
              <span class="text-xs font-semibold px-2.5 py-0.5 rounded-full bg-indigo-500/20 text-indigo-300 border border-indigo-500/30">CCTV Manager</span>
            </h1>
            <p class="text-xs text-slate-400">මිල ගණන් සහ තොග කළමනාකරණ පද්ධතිය</p>
          </div>
        </div>

        <div class="flex md:hidden items-center gap-2">
          <button onclick="openModal('addModal')" class="bg-indigo-600 hover:bg-indigo-500 text-white p-2 rounded-lg flex items-center justify-center">
            <i data-lucide="plus" class="w-5 h-5"></i>
          </button>
        </div>
      </div>

      <!-- Action Buttons -->
      <div class="flex flex-wrap items-center justify-end gap-2.5 w-full md:w-auto">
        
        <!-- Live Storage Indicator -->
        <div class="hidden lg:flex items-center gap-2 px-3 py-1.5 rounded-lg bg-emerald-500/10 border border-emerald-500/20 text-emerald-400 text-xs">
          <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
          <span>Auto-Saved in Browser</span>
        </div>

        <!-- Add New Product Button -->
        <button onclick="openModal('addModal')" class="bg-gradient-to-r from-indigo-600 to-indigo-500 hover:from-indigo-500 hover:to-indigo-400 text-white font-medium text-sm px-3.5 py-2 rounded-xl shadow-lg shadow-indigo-600/20 transition-all flex items-center gap-2">
          <i data-lucide="plus-circle" class="w-4 h-4"></i>
          <span>Add Product</span>
        </button>

        <!-- WhatsApp Share Button -->
        <button onclick="openWhatsAppModal()" class="bg-emerald-600 hover:bg-emerald-500 text-white font-medium text-sm px-3.5 py-2 rounded-xl shadow-lg shadow-emerald-600/20 transition-all flex items-center gap-2">
          <i data-lucide="message-square" class="w-4 h-4"></i>
          <span>WhatsApp List</span>
        </button>

        <!-- Print Button -->
        <button onclick="window.print()" class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium text-sm px-3 py-2 rounded-xl transition-all flex items-center gap-1.5">
          <i data-lucide="printer" class="w-4 h-4"></i>
          <span class="hidden sm:inline">Print</span>
        </button>

        <!-- Export Backup -->
        <button onclick="exportJSON()" class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium text-sm px-3 py-2 rounded-xl transition-all flex items-center gap-1.5" title="Download backup file">
          <i data-lucide="download" class="w-4 h-4"></i>
          <span class="hidden sm:inline">Export</span>
        </button>

        <!-- Restore Backup -->
        <label class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium text-sm px-3 py-2 rounded-xl transition-all flex items-center gap-1.5 cursor-pointer" title="Restore from backup file">
          <i data-lucide="upload" class="w-4 h-4"></i>
          <span class="hidden sm:inline">Restore</span>
          <input type="file" id="importFileInput" accept=".json" class="hidden" onchange="importJSON(event)">
        </label>

        <!-- Reset Button -->
        <button onclick="confirmReset()" class="bg-rose-500/10 hover:bg-rose-500/20 text-rose-400 border border-rose-500/20 p-2 rounded-xl transition-all" title="Reset to default items">
          <i data-lucide="rotate-ccw" class="w-4 h-4"></i>
        </button>
      </div>

    </div>
  </header>

  <!-- MAIN CONTAINER -->
  <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex-1 w-full space-y-6">

    <!-- SEARCH & FILTER BAR -->
    <div class="bg-slate-800 border border-slate-700 rounded-2xl p-4 shadow-xl no-print backdrop-blur-md">
      <div class="grid grid-cols-1 md:grid-cols-12 gap-3">
        
        <!-- Live Search Box -->
        <div class="md:col-span-5 relative">
          <div class="absolute inset-y-0 left-0 pl-3.5 flex items-center pointer-events-none text-slate-400">
            <i data-lucide="search" class="w-5 h-5"></i>
          </div>
          <input 
            type="text" 
            id="searchInput" 
            placeholder="Search CCTV model, brand, WiFi, 4G..." 
            oninput="renderProducts()"
            class="w-full pl-10 pr-4 py-2.5 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 placeholder-slate-500"
          >
        </div>

        <!-- Brand Filter Dropdown -->
        <div class="md:col-span-3">
          <select id="brandFilter" onchange="renderProducts()" class="w-full py-2.5 px-3 bg-slate-900 border border-slate-700 text-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
            <option value="ALL">All Brands (සියලුම සන්නාම)</option>
            <option value="Hikvision">Hikvision</option>
            <option value="Dahua">Dahua</option>
            <option value="Imou">Imou</option>
            <option value="Ezviz">Ezviz</option>
            <option value="Tiandy">Tiandy</option>
            <option value="Baseus">Baseus</option>
            <option value="Other">Other</option>
          </select>
        </div>

        <!-- Category Filter Dropdown -->
        <div class="md:col-span-3">
          <select id="categoryFilter" onchange="renderProducts()" class="w-full py-2.5 px-3 bg-slate-900 border border-slate-700 text-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500

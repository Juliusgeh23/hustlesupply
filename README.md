<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HUSTLE SUPPLY - Crafted for the Grind</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');
        
        body {
            font-family: 'Inter', sans-serif;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
        }
        
        .hover-scale {
            transition: transform 0.3s ease;
        }
        
        .hover-scale:hover {
            transform: scale(1.05);
        }
        
        .cart-count {
            animation: pulse 0.5s ease-in-out;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        
        .product-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .modal {
            backdrop-filter: blur(10px);
        }
        
        .section {
            display: none;
        }
        
        .section.active {
            display: block;
        }
        
        .admin-tab {
            display: none;
        }
        
        .admin-tab.active {
            display: block;
        }
        
        /* Light Mode Styles */
        .light-mode {
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%) !important;
            color: #1a202c !important;
        }
        
        .light-mode .product-card {
            background: rgba(255, 255, 255, 0.8) !important;
            border: 1px solid rgba(0, 0, 0, 0.1) !important;
            color: #1a202c !important;
        }
        
        .light-mode header {
            background: rgba(255, 255, 255, 0.9) !important;
            border-color: #e2e8f0 !important;
        }
        
        .light-mode footer {
            border-color: #e2e8f0 !important;
        }
        
        .light-mode .bg-gray-800 {
            background-color: #f7fafc !important;
            color: #1a202c !important;
        }
        
        .light-mode .bg-gray-900 {
            background-color: #ffffff !important;
            color: #1a202c !important;
        }
        
        .light-mode .text-gray-300 {
            color: #4a5568 !important;
        }
        
        .light-mode .text-gray-400 {
            color: #718096 !important;
        }
        
        .light-mode .border-gray-700 {
            border-color: #e2e8f0 !important;
        }
        
        /* Background slideshow */
        .slideshow-bg {
            background-size: cover !important;
            background-position: center !important;
            background-repeat: no-repeat !important;
            transition: background-image 1s ease-in-out !important;
        }
    </style>
</head>
<body class="gradient-bg text-white min-h-screen">
    <!-- Header -->
    <header class="border-b border-gray-700 sticky top-0 z-50 backdrop-blur-md bg-black/50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <!-- Logo -->
                <div class="flex items-center space-x-2 cursor-pointer" onclick="showSection('home')">
                    <div class="w-8 h-8 bg-gradient-to-r from-orange-500 to-red-500 rounded-sm flex items-center justify-center">
                        <span class="text-white font-black text-sm">H</span>
                    </div>
                    <div>
                        <h1 class="text-xl font-black tracking-tight flex items-center space-x-1">
                            <span>HUSTLE</span>
                            <span class="text-lg">🔥</span>
                            <span>SUPPLY</span>
                            <span class="text-lg">💎</span>
                        </h1>
                        <p class="text-xs text-gray-400 -mt-1 flex items-center space-x-1">
                            <span>🏙️</span>
                            <span>Crafted for the Grind</span>
                            <span>⚡</span>
                        </p>
                    </div>
                </div>
                
                <!-- Navigation -->
                <nav class="hidden md:flex space-x-8">
                    <a href="#" onclick="showSection('shop')" class="text-gray-300 hover:text-white transition-colors font-medium">Shop</a>
                    <a href="#" onclick="showSection('collections')" class="text-gray-300 hover:text-white transition-colors font-medium">Collections</a>
                    <a href="#" onclick="showSection('about')" class="text-gray-300 hover:text-white transition-colors font-medium">About</a>
                    <a href="#" onclick="showSection('contact')" class="text-gray-300 hover:text-white transition-colors font-medium">Contact</a>
                </nav>
                
                <!-- User Actions -->
                <div class="flex items-center space-x-4">
                    <!-- Theme Toggle -->
                    <button onclick="toggleTheme()" class="p-2 hover:bg-gray-800 rounded-lg transition-colors" title="Toggle Light/Dark Mode">
                        <svg id="theme-icon" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path>
                        </svg>
                    </button>
                    
                    <!-- Currency Selector -->
                    <select id="currency-selector" class="bg-gray-800 border border-gray-700 rounded px-2 py-1 text-sm text-white focus:border-orange-500 focus:outline-none">
                        <option value="USD">USD</option>
                        <option value="EUR">EUR</option>
                        <option value="GBP">GBP</option>
                        <option value="NGN">NGN</option>
                        <option value="INR">INR</option>
                        <option value="CAD">CAD</option>
                        <option value="AUD">AUD</option>
                        <option value="JPY">JPY</option>
                    </select>
                    
                    <div id="user-menu" class="hidden flex items-center space-x-2">
                        <div class="relative">
                            <img id="user-avatar" src="" alt="Profile" class="w-8 h-8 rounded-full bg-gray-600 hidden">
                            <div id="user-avatar-placeholder" class="w-8 h-8 rounded-full bg-gradient-to-r from-orange-500 to-red-500 flex items-center justify-center">
                                <span id="user-initial" class="text-white text-sm font-bold"></span>
                            </div>
                            <button onclick="showModal('profile')" class="absolute -bottom-1 -right-1 w-4 h-4 bg-orange-500 rounded-full flex items-center justify-center hover:bg-orange-600 transition-colors">
                                <svg class="w-2 h-2 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path>
                                </svg>
                            </button>
                        </div>
                        <span id="user-name" class="text-sm text-gray-300"></span>
                        <button onclick="logout()" class="text-gray-400 hover:text-white text-sm">Logout</button>
                        <button id="admin-btn" onclick="showSection('admin')" class="ml-2 text-orange-400 hover:text-orange-300 text-sm hidden">Admin</button>
                    </div>
                    <div id="auth-buttons">
                        <button onclick="showModal('login')" class="text-gray-300 hover:text-white text-sm mr-2">Login</button>
                        <button onclick="showModal('signup')" class="bg-orange-500 hover:bg-orange-600 px-3 py-1 rounded text-sm">Sign Up</button>
                    </div>
                    <button onclick="toggleCart()" class="relative p-2 hover:bg-gray-800 rounded-lg transition-colors">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4m0 0L7 13m0 0l-2.5 5M7 13l2.5 5m6-5v6a2 2 0 01-2 2H9a2 2 0 01-2-2v-6m8 0V9a2 2 0 00-2-2H9a2 2 0 00-2 2v4.01"></path>
                        </svg>
                        <span id="cart-count" class="absolute -top-1 -right-1 bg-orange-500 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center">0</span>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Home Section -->
    <section id="home" class="section active">
        <!-- Hero Section -->
        <div id="hero-section" class="relative py-20 px-4 min-h-screen flex items-center">
            <div class="absolute inset-0 bg-black bg-opacity-50 z-10"></div>
            <div class="max-w-7xl mx-auto text-center relative z-20">
                <h2 class="text-5xl md:text-7xl font-black mb-6 bg-gradient-to-r from-white to-gray-400 bg-clip-text text-transparent flex items-center justify-center space-x-4">
                    <span class="text-4xl md:text-6xl">🔥</span>
                    <span>STREET READY</span>
                    <span class="text-4xl md:text-6xl">💎</span>
                </h2>
                <p class="text-xl md:text-2xl text-gray-300 mb-8 max-w-2xl mx-auto flex items-center justify-center space-x-2">
                    <span class="text-2xl">🏙️</span>
                    <span>Premium streetwear designed for those who never stop grinding. Every piece tells your story.</span>
                    <span class="text-2xl">⚡</span>
                </p>
                <button onclick="showSection('shop')" class="bg-gradient-to-r from-orange-500 to-red-500 text-white px-8 py-4 rounded-lg font-bold text-lg hover:from-orange-600 hover:to-red-600 transition-all transform hover:scale-105 flex items-center space-x-2 mx-auto">
                    <span class="text-xl">🛍️</span>
                    <span>SHOP NOW</span>
                    <span class="text-xl">🚀</span>
                </button>
            </div>
        </div>

        <!-- Featured Products Preview -->
        <div class="py-16 px-4">
            <div class="max-w-7xl mx-auto">
                <h3 class="text-3xl font-black mb-12 text-center">FEATURED DROPS</h3>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8" id="featured-products">
                    <!-- Products will be loaded here -->
                </div>
                <div class="text-center mt-8">
                    <button onclick="showSection('shop')" class="bg-white text-black px-6 py-3 rounded-lg font-bold hover:bg-gray-200 transition-colors">
                        VIEW ALL PRODUCTS
                    </button>
                </div>
            </div>
            
            <!-- Customer Service Tab -->
            <div id="admin-customer-service" class="admin-tab">
                <div class="space-y-8">
                    <!-- Customer Messages -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Customer Messages</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-blue-500" id="unread-messages">0 Unread</span>
                            </div>
                        </div>
                        <div id="customer-messages" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No customer messages</p>
                        </div>
                    </div>
                    
                    <!-- Product Reviews & Ratings -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Product Reviews & Ratings</h3>
                        <div id="product-reviews" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No product reviews yet</p>
                        </div>
                    </div>
                    
                    <!-- Quick Response Templates -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Quick Response Templates</h3>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                            <div>
                                <h4 class="text-lg font-bold mb-4">Add Template</h4>
                                <form id="response-template-form" class="space-y-4">
                                    <input type="text" id="template-name" placeholder="Template Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    <textarea id="template-content" placeholder="Template Content" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                                    <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                        ADD TEMPLATE
                                    </button>
                                </form>
                            </div>
                            <div>
                                <h4 class="text-lg font-bold mb-4">Saved Templates</h4>
                                <div id="response-templates" class="space-y-2 max-h-64 overflow-y-auto">
                                    <p class="text-gray-400 text-center py-8">No templates saved</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Attack Monitor Tab -->
            <div id="admin-attack-monitor" class="admin-tab">
                <div class="space-y-8">
                    <!-- Attack Statistics -->
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-red-500">
                            <h3 class="text-lg font-bold mb-2 text-red-400">Total Attacks</h3>
                            <p class="text-3xl text-red-500 font-black" id="total-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-orange-500">
                            <h3 class="text-lg font-bold mb-2 text-orange-400">Today's Attacks</h3>
                            <p class="text-3xl text-orange-500 font-black" id="today-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-yellow-500">
                            <h3 class="text-lg font-bold mb-2 text-yellow-400">Code Inspection</h3>
                            <p class="text-3xl text-yellow-500 font-black" id="code-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-purple-500">
                            <h3 class="text-lg font-bold mb-2 text-purple-400">Right-Click Attempts</h3>
                            <p class="text-3xl text-purple-500 font-black" id="rightclick-attacks">0</p>
                        </div>
                    </div>
                    
                    <!-- Live Attack Feed -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold text-red-400">🚨 Live Attack Monitor</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-red-500">MONITORING</span>
                            </div>
                        </div>
                        <div id="attack-feed" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No attack attempts detected</p>
                        </div>
                    </div>
                    
                    <!-- Attack Details Table -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Attack Attempt Details</h3>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left">
                                <thead>
                                    <tr class="border-b border-gray-700">
                                        <th class="pb-3 font-bold">Time</th>
                                        <th class="pb-3 font-bold">Attack Type</th>
                                        <th class="pb-3 font-bold">Details</th>
                                        <th class="pb-3 font-bold">Location</th>
                                        <th class="pb-3 font-bold">User Agent</th>
                                        <th class="pb-3 font-bold">Severity</th>
                                    </tr>
                                </thead>
                                <tbody id="attack-details-table">
                                    <!-- Attack details will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                    
                    <!-- Attack Response Actions -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6 text-red-400">🛡️ Security Response</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="clearAttackLogs()" class="bg-red-600 hover:bg-red-700 text-white py-3 px-4 rounded-lg font-bold">
                                🗑️ Clear Attack Logs
                            </button>
                            <button onclick="exportAttackData()" class="bg-orange-600 hover:bg-orange-700 text-white py-3 px-4 rounded-lg font-bold">
                                📊 Export Attack Data
                            </button>
                            <button onclick="blockSuspiciousIPs()" class="bg-purple-600 hover:bg-purple-700 text-white py-3 px-4 rounded-lg font-bold">
                                🚫 Block Suspicious IPs
                            </button>
                        </div>
                        
                        <div class="mt-6 p-4 bg-red-900/30 border border-red-500/30 rounded-lg">
                            <h4 class="text-red-400 font-bold mb-2">🔒 Security Status</h4>
                            <p class="text-sm text-red-300">All code inspection attempts are being monitored and logged. Attackers will be warned and their activities recorded.</p>
                            <p class="text-xs text-gray-400 mt-2">Last security scan: <span id="last-security-scan">Just now</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Shop Section -->
    <section id="shop" class="section py-16 px-4">
        <div class="max-w-7xl mx-auto">
            <h2 class="text-4xl font-black mb-8">SHOP ALL</h2>
            
            <!-- Filter Bar -->
            <div class="flex flex-wrap gap-4 mb-8">
                <button onclick="filterProducts('all')" class="filter-btn active bg-orange-500 text-white px-4 py-2 rounded-lg font-medium">All</button>
                <button onclick="filterProducts('tees')" class="filter-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Tees</button>
                <button onclick="filterProducts('hoodies')" class="filter-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Hoodies</button>
                <button onclick="filterProducts('bottoms')" class="filter-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Bottoms</button>
                <button onclick="filterProducts('accessories')" class="filter-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Accessories</button>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8" id="all-products">
                <!-- Products will be loaded here -->
            </div>
            
            <!-- Pagination -->
            <div id="pagination" class="flex justify-center items-center space-x-4 mt-8">
                <button id="prev-page" onclick="changePage(-1)" class="bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium disabled:opacity-50 disabled:cursor-not-allowed">Previous</button>
                <span id="page-info" class="text-gray-300">Page 1 of 1</span>
                <button id="next-page" onclick="changePage(1)" class="bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium disabled:opacity-50 disabled:cursor-not-allowed">Next</button>
            </div>
            
            <!-- Customer Service Tab -->
            <div id="admin-customer-service" class="admin-tab">
                <div class="space-y-8">
                    <!-- Customer Messages -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Customer Messages</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-blue-500" id="unread-messages">0 Unread</span>
                            </div>
                        </div>
                        <div id="customer-messages" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No customer messages</p>
                        </div>
                    </div>
                    
                    <!-- Product Reviews & Ratings -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Product Reviews & Ratings</h3>
                        <div id="product-reviews" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No product reviews yet</p>
                        </div>
                    </div>
                    
                    <!-- Quick Response Templates -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Quick Response Templates</h3>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                            <div>
                                <h4 class="text-lg font-bold mb-4">Add Template</h4>
                                <form id="response-template-form" class="space-y-4">
                                    <input type="text" id="template-name" placeholder="Template Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    <textarea id="template-content" placeholder="Template Content" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                                    <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                        ADD TEMPLATE
                                    </button>
                                </form>
                            </div>
                            <div>
                                <h4 class="text-lg font-bold mb-4">Saved Templates</h4>
                                <div id="response-templates" class="space-y-2 max-h-64 overflow-y-auto">
                                    <p class="text-gray-400 text-center py-8">No templates saved</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Attack Monitor Tab -->
            <div id="admin-attack-monitor" class="admin-tab">
                <div class="space-y-8">
                    <!-- Attack Statistics -->
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-red-500">
                            <h3 class="text-lg font-bold mb-2 text-red-400">Total Attacks</h3>
                            <p class="text-3xl text-red-500 font-black" id="total-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-orange-500">
                            <h3 class="text-lg font-bold mb-2 text-orange-400">Today's Attacks</h3>
                            <p class="text-3xl text-orange-500 font-black" id="today-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-yellow-500">
                            <h3 class="text-lg font-bold mb-2 text-yellow-400">Code Inspection</h3>
                            <p class="text-3xl text-yellow-500 font-black" id="code-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-purple-500">
                            <h3 class="text-lg font-bold mb-2 text-purple-400">Right-Click Attempts</h3>
                            <p class="text-3xl text-purple-500 font-black" id="rightclick-attacks">0</p>
                        </div>
                    </div>
                    
                    <!-- Live Attack Feed -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold text-red-400">🚨 Live Attack Monitor</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-red-500">MONITORING</span>
                            </div>
                        </div>
                        <div id="attack-feed" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No attack attempts detected</p>
                        </div>
                    </div>
                    
                    <!-- Attack Details Table -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Attack Attempt Details</h3>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left">
                                <thead>
                                    <tr class="border-b border-gray-700">
                                        <th class="pb-3 font-bold">Time</th>
                                        <th class="pb-3 font-bold">Attack Type</th>
                                        <th class="pb-3 font-bold">Details</th>
                                        <th class="pb-3 font-bold">Location</th>
                                        <th class="pb-3 font-bold">User Agent</th>
                                        <th class="pb-3 font-bold">Severity</th>
                                    </tr>
                                </thead>
                                <tbody id="attack-details-table">
                                    <!-- Attack details will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                    
                    <!-- Attack Response Actions -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6 text-red-400">🛡️ Security Response</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="clearAttackLogs()" class="bg-red-600 hover:bg-red-700 text-white py-3 px-4 rounded-lg font-bold">
                                🗑️ Clear Attack Logs
                            </button>
                            <button onclick="exportAttackData()" class="bg-orange-600 hover:bg-orange-700 text-white py-3 px-4 rounded-lg font-bold">
                                📊 Export Attack Data
                            </button>
                            <button onclick="blockSuspiciousIPs()" class="bg-purple-600 hover:bg-purple-700 text-white py-3 px-4 rounded-lg font-bold">
                                🚫 Block Suspicious IPs
                            </button>
                        </div>
                        
                        <div class="mt-6 p-4 bg-red-900/30 border border-red-500/30 rounded-lg">
                            <h4 class="text-red-400 font-bold mb-2">🔒 Security Status</h4>
                            <p class="text-sm text-red-300">All code inspection attempts are being monitored and logged. Attackers will be warned and their activities recorded.</p>
                            <p class="text-xs text-gray-400 mt-2">Last security scan: <span id="last-security-scan">Just now</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Collections Section -->
    <section id="collections" class="section py-16 px-4">
        <div class="max-w-7xl mx-auto">
            <h2 class="text-4xl font-black mb-8">COLLECTIONS</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="product-card rounded-xl p-8 hover-scale cursor-pointer" onclick="filterProducts('essentials')">
                    <div class="text-center">
                        <h3 class="text-2xl font-bold mb-4">ESSENTIALS</h3>
                        <p class="text-gray-400 mb-6">Core pieces for everyday grind</p>
                        <div class="flex justify-center space-x-2 mb-4">
                            <span class="text-3xl">👕</span>
                            <span class="text-3xl">🧥</span>
                            <span class="text-3xl">👖</span>
                        </div>
                        <button class="bg-white text-black px-6 py-2 rounded-lg font-bold">EXPLORE</button>
                    </div>
                </div>
                
                <div class="product-card rounded-xl p-8 hover-scale cursor-pointer" onclick="filterProducts('limited')">
                    <div class="text-center">
                        <h3 class="text-2xl font-bold mb-4">LIMITED EDITION</h3>
                        <p class="text-gray-400 mb-6">Exclusive drops for true hustlers</p>
                        <div class="flex justify-center space-x-2 mb-4">
                            <span class="text-3xl">⭐</span>
                            <span class="text-3xl">🔥</span>
                            <span class="text-3xl">💎</span>
                        </div>
                        <button class="bg-white text-black px-6 py-2 rounded-lg font-bold">EXPLORE</button>
                    </div>
                </div>
                
                <div class="product-card rounded-xl p-8 hover-scale cursor-pointer" onclick="filterProducts('accessories')">
                    <div class="text-center">
                        <h3 class="text-2xl font-bold mb-4">ACCESSORIES</h3>
                        <p class="text-gray-400 mb-6">Complete your hustle look</p>
                        <div class="flex justify-center space-x-2 mb-4">
                            <span class="text-3xl">🧢</span>
                            <span class="text-3xl">🎒</span>
                            <span class="text-3xl">👟</span>
                        </div>
                        <button class="bg-white text-black px-6 py-2 rounded-lg font-bold">EXPLORE</button>
                    </div>
                </div>
                
                <div class="product-card rounded-xl p-8 hover-scale cursor-pointer" onclick="filterProducts('new')">
                    <div class="text-center">
                        <h3 class="text-2xl font-bold mb-4">NEW ARRIVALS</h3>
                        <p class="text-gray-400 mb-6">Fresh drops, hot off the press</p>
                        <div class="flex justify-center space-x-2 mb-4">
                            <span class="text-3xl">🆕</span>
                            <span class="text-3xl">🚀</span>
                            <span class="text-3xl">✨</span>
                        </div>
                        <button class="bg-white text-black px-6 py-2 rounded-lg font-bold">EXPLORE</button>
                    </div>
                </div>
            </div>
            
            <!-- Customer Service Tab -->
            <div id="admin-customer-service" class="admin-tab">
                <div class="space-y-8">
                    <!-- Customer Messages -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Customer Messages</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-blue-500" id="unread-messages">0 Unread</span>
                            </div>
                        </div>
                        <div id="customer-messages" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No customer messages</p>
                        </div>
                    </div>
                    
                    <!-- Product Reviews & Ratings -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Product Reviews & Ratings</h3>
                        <div id="product-reviews" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No product reviews yet</p>
                        </div>
                    </div>
                    
                    <!-- Quick Response Templates -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Quick Response Templates</h3>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                            <div>
                                <h4 class="text-lg font-bold mb-4">Add Template</h4>
                                <form id="response-template-form" class="space-y-4">
                                    <input type="text" id="template-name" placeholder="Template Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    <textarea id="template-content" placeholder="Template Content" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                                    <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                        ADD TEMPLATE
                                    </button>
                                </form>
                            </div>
                            <div>
                                <h4 class="text-lg font-bold mb-4">Saved Templates</h4>
                                <div id="response-templates" class="space-y-2 max-h-64 overflow-y-auto">
                                    <p class="text-gray-400 text-center py-8">No templates saved</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Attack Monitor Tab -->
            <div id="admin-attack-monitor" class="admin-tab">
                <div class="space-y-8">
                    <!-- Attack Statistics -->
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-red-500">
                            <h3 class="text-lg font-bold mb-2 text-red-400">Total Attacks</h3>
                            <p class="text-3xl text-red-500 font-black" id="total-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-orange-500">
                            <h3 class="text-lg font-bold mb-2 text-orange-400">Today's Attacks</h3>
                            <p class="text-3xl text-orange-500 font-black" id="today-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-yellow-500">
                            <h3 class="text-lg font-bold mb-2 text-yellow-400">Code Inspection</h3>
                            <p class="text-3xl text-yellow-500 font-black" id="code-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-purple-500">
                            <h3 class="text-lg font-bold mb-2 text-purple-400">Right-Click Attempts</h3>
                            <p class="text-3xl text-purple-500 font-black" id="rightclick-attacks">0</p>
                        </div>
                    </div>
                    
                    <!-- Live Attack Feed -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold text-red-400">🚨 Live Attack Monitor</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-red-500">MONITORING</span>
                            </div>
                        </div>
                        <div id="attack-feed" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No attack attempts detected</p>
                        </div>
                    </div>
                    
                    <!-- Attack Details Table -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Attack Attempt Details</h3>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left">
                                <thead>
                                    <tr class="border-b border-gray-700">
                                        <th class="pb-3 font-bold">Time</th>
                                        <th class="pb-3 font-bold">Attack Type</th>
                                        <th class="pb-3 font-bold">Details</th>
                                        <th class="pb-3 font-bold">Location</th>
                                        <th class="pb-3 font-bold">User Agent</th>
                                        <th class="pb-3 font-bold">Severity</th>
                                    </tr>
                                </thead>
                                <tbody id="attack-details-table">
                                    <!-- Attack details will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                    
                    <!-- Attack Response Actions -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6 text-red-400">🛡️ Security Response</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="clearAttackLogs()" class="bg-red-600 hover:bg-red-700 text-white py-3 px-4 rounded-lg font-bold">
                                🗑️ Clear Attack Logs
                            </button>
                            <button onclick="exportAttackData()" class="bg-orange-600 hover:bg-orange-700 text-white py-3 px-4 rounded-lg font-bold">
                                📊 Export Attack Data
                            </button>
                            <button onclick="blockSuspiciousIPs()" class="bg-purple-600 hover:bg-purple-700 text-white py-3 px-4 rounded-lg font-bold">
                                🚫 Block Suspicious IPs
                            </button>
                        </div>
                        
                        <div class="mt-6 p-4 bg-red-900/30 border border-red-500/30 rounded-lg">
                            <h4 class="text-red-400 font-bold mb-2">🔒 Security Status</h4>
                            <p class="text-sm text-red-300">All code inspection attempts are being monitored and logged. Attackers will be warned and their activities recorded.</p>
                            <p class="text-xs text-gray-400 mt-2">Last security scan: <span id="last-security-scan">Just now</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section py-16 px-4">
        <div class="max-w-4xl mx-auto">
            <h2 class="text-4xl font-black mb-8 text-center">ABOUT HUSTLE SUPPLY</h2>
            
            <div class="text-center mb-12">
                <p class="text-xl text-gray-300 mb-6">
                    Born from the streets, crafted for the grind. HUSTLE SUPPLY represents more than just clothing – it's a mindset.
                </p>
                <p class="text-gray-400 leading-relaxed">
                    Founded in 2024, we believe that success isn't given, it's earned. Every thread, every stitch, every design tells the story of those who refuse to settle. Our premium streetwear is designed for the relentless, the ambitious, and the unstoppable.
                </p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-12">
                <div class="text-center">
                    <div class="w-16 h-16 bg-gradient-to-r from-orange-500 to-red-500 rounded-full mx-auto mb-4 flex items-center justify-center">
                        <span class="text-2xl">💪</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">BUILT TO LAST</h3>
                    <p class="text-gray-400">Premium materials that withstand the daily grind</p>
                </div>
                
                <div class="text-center">
                    <div class="w-16 h-16 bg-gradient-to-r from-orange-500 to-red-500 rounded-full mx-auto mb-4 flex items-center justify-center">
                        <span class="text-2xl">🎨</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">UNIQUE DESIGNS</h3>
                    <p class="text-gray-400">Original artwork that speaks to the hustle culture</p>
                </div>
                
                <div class="text-center">
                    <div class="w-16 h-16 bg-gradient-to-r from-orange-500 to-red-500 rounded-full mx-auto mb-4 flex items-center justify-center">
                        <span class="text-2xl">🌍</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">GLOBAL COMMUNITY</h3>
                    <p class="text-gray-400">Connecting hustlers worldwide through fashion</p>
                </div>
            </div>
            
            <div class="product-card rounded-xl p-8">
                <h3 class="text-2xl font-bold mb-4">OUR MISSION</h3>
                <p class="text-gray-300 leading-relaxed">
                    To empower the next generation of entrepreneurs, creators, and dreamers with clothing that reflects their ambition. We're not just selling apparel – we're building a movement of individuals who understand that success is a choice, and every day is an opportunity to level up.
                </p>
            </div>
            
            <!-- Customer Service Tab -->
            <div id="admin-customer-service" class="admin-tab">
                <div class="space-y-8">
                    <!-- Customer Messages -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Customer Messages</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-blue-500" id="unread-messages">0 Unread</span>
                            </div>
                        </div>
                        <div id="customer-messages" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No customer messages</p>
                        </div>
                    </div>
                    
                    <!-- Product Reviews & Ratings -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Product Reviews & Ratings</h3>
                        <div id="product-reviews" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No product reviews yet</p>
                        </div>
                    </div>
                    
                    <!-- Quick Response Templates -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Quick Response Templates</h3>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                            <div>
                                <h4 class="text-lg font-bold mb-4">Add Template</h4>
                                <form id="response-template-form" class="space-y-4">
                                    <input type="text" id="template-name" placeholder="Template Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    <textarea id="template-content" placeholder="Template Content" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                                    <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                        ADD TEMPLATE
                                    </button>
                                </form>
                            </div>
                            <div>
                                <h4 class="text-lg font-bold mb-4">Saved Templates</h4>
                                <div id="response-templates" class="space-y-2 max-h-64 overflow-y-auto">
                                    <p class="text-gray-400 text-center py-8">No templates saved</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Attack Monitor Tab -->
            <div id="admin-attack-monitor" class="admin-tab">
                <div class="space-y-8">
                    <!-- Attack Statistics -->
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-red-500">
                            <h3 class="text-lg font-bold mb-2 text-red-400">Total Attacks</h3>
                            <p class="text-3xl text-red-500 font-black" id="total-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-orange-500">
                            <h3 class="text-lg font-bold mb-2 text-orange-400">Today's Attacks</h3>
                            <p class="text-3xl text-orange-500 font-black" id="today-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-yellow-500">
                            <h3 class="text-lg font-bold mb-2 text-yellow-400">Code Inspection</h3>
                            <p class="text-3xl text-yellow-500 font-black" id="code-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-purple-500">
                            <h3 class="text-lg font-bold mb-2 text-purple-400">Right-Click Attempts</h3>
                            <p class="text-3xl text-purple-500 font-black" id="rightclick-attacks">0</p>
                        </div>
                    </div>
                    
                    <!-- Live Attack Feed -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold text-red-400">🚨 Live Attack Monitor</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-red-500">MONITORING</span>
                            </div>
                        </div>
                        <div id="attack-feed" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No attack attempts detected</p>
                        </div>
                    </div>
                    
                    <!-- Attack Details Table -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Attack Attempt Details</h3>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left">
                                <thead>
                                    <tr class="border-b border-gray-700">
                                        <th class="pb-3 font-bold">Time</th>
                                        <th class="pb-3 font-bold">Attack Type</th>
                                        <th class="pb-3 font-bold">Details</th>
                                        <th class="pb-3 font-bold">Location</th>
                                        <th class="pb-3 font-bold">User Agent</th>
                                        <th class="pb-3 font-bold">Severity</th>
                                    </tr>
                                </thead>
                                <tbody id="attack-details-table">
                                    <!-- Attack details will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                    
                    <!-- Attack Response Actions -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6 text-red-400">🛡️ Security Response</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="clearAttackLogs()" class="bg-red-600 hover:bg-red-700 text-white py-3 px-4 rounded-lg font-bold">
                                🗑️ Clear Attack Logs
                            </button>
                            <button onclick="exportAttackData()" class="bg-orange-600 hover:bg-orange-700 text-white py-3 px-4 rounded-lg font-bold">
                                📊 Export Attack Data
                            </button>
                            <button onclick="blockSuspiciousIPs()" class="bg-purple-600 hover:bg-purple-700 text-white py-3 px-4 rounded-lg font-bold">
                                🚫 Block Suspicious IPs
                            </button>
                        </div>
                        
                        <div class="mt-6 p-4 bg-red-900/30 border border-red-500/30 rounded-lg">
                            <h4 class="text-red-400 font-bold mb-2">🔒 Security Status</h4>
                            <p class="text-sm text-red-300">All code inspection attempts are being monitored and logged. Attackers will be warned and their activities recorded.</p>
                            <p class="text-xs text-gray-400 mt-2">Last security scan: <span id="last-security-scan">Just now</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section py-16 px-4">
        <div class="max-w-4xl mx-auto">
            <h2 class="text-4xl font-black mb-8 text-center">GET IN TOUCH</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div>
                    <h3 class="text-2xl font-bold mb-6">CONTACT INFO</h3>
                    <div class="space-y-4">
                        <div class="flex items-center space-x-3">
                            <span class="text-orange-500">📧</span>
                            <span>hello@hustlesupply.com</span>
                        </div>
                        <div class="flex items-center space-x-3">
                            <span class="text-orange-500">📱</span>
                            <span>+1 (555) 123-HUSTLE</span>
                        </div>
                        <div class="flex items-center space-x-3">
                            <span class="text-orange-500">📍</span>
                            <span>123 Grind Street, Hustle City, HC 12345</span>
                        </div>
                        <div class="flex items-center space-x-3">
                            <span class="text-orange-500">🕒</span>
                            <span>Mon-Fri: 9AM-6PM PST</span>
                        </div>
                    </div>
                    
                    <div class="mt-8">
                        <h4 class="text-lg font-bold mb-4">FOLLOW THE GRIND</h4>
                        <div class="flex space-x-4">
                            <a href="#" class="text-gray-400 hover:text-white transition-colors">
                                <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                                    <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
                                </svg>
                            </a>
                            <a href="#" class="text-gray-400 hover:text-white transition-colors">
                                <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                                    <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                                </svg>
                            </a>
                        </div>
                    </div>
                </div>
                
                <div class="product-card rounded-xl p-6">
                    <h3 class="text-2xl font-bold mb-6">SEND MESSAGE</h3>
                    <form id="contact-page-form" class="space-y-4">
                        <div>
                            <input type="text" id="contact-name" placeholder="Your Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                        </div>
                        <div>
                            <input type="email" id="contact-email-field" placeholder="Your Email" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                        </div>
                        <div>
                            <select id="contact-subject" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                                <option value="">Select Subject</option>
                                <option value="general">General Inquiry</option>
                                <option value="support">Customer Support</option>
                                <option value="business">Business Partnership</option>
                                <option value="press">Press & Media</option>
                                <option value="feedback">Feedback</option>
                            </select>
                        </div>
                        <div>
                            <textarea id="contact-message-field" placeholder="Your Message" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                        </div>
                        <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                            SEND MESSAGE
                        </button>
                        <p class="text-xs text-gray-400 text-center">
                            💬 Messages are sent directly to our admin team for quick response
                        </p>
                    </form>
                </div>
            </div>
            
            <!-- Customer Service Tab -->
            <div id="admin-customer-service" class="admin-tab">
                <div class="space-y-8">
                    <!-- Customer Messages -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Customer Messages</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-blue-500" id="unread-messages">0 Unread</span>
                            </div>
                        </div>
                        <div id="customer-messages" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No customer messages</p>
                        </div>
                    </div>
                    
                    <!-- Product Reviews & Ratings -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Product Reviews & Ratings</h3>
                        <div id="product-reviews" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No product reviews yet</p>
                        </div>
                    </div>
                    
                    <!-- Quick Response Templates -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Quick Response Templates</h3>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                            <div>
                                <h4 class="text-lg font-bold mb-4">Add Template</h4>
                                <form id="response-template-form" class="space-y-4">
                                    <input type="text" id="template-name" placeholder="Template Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    <textarea id="template-content" placeholder="Template Content" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                                    <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                        ADD TEMPLATE
                                    </button>
                                </form>
                            </div>
                            <div>
                                <h4 class="text-lg font-bold mb-4">Saved Templates</h4>
                                <div id="response-templates" class="space-y-2 max-h-64 overflow-y-auto">
                                    <p class="text-gray-400 text-center py-8">No templates saved</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Attack Monitor Tab -->
            <div id="admin-attack-monitor" class="admin-tab">
                <div class="space-y-8">
                    <!-- Attack Statistics -->
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-red-500">
                            <h3 class="text-lg font-bold mb-2 text-red-400">Total Attacks</h3>
                            <p class="text-3xl text-red-500 font-black" id="total-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-orange-500">
                            <h3 class="text-lg font-bold mb-2 text-orange-400">Today's Attacks</h3>
                            <p class="text-3xl text-orange-500 font-black" id="today-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-yellow-500">
                            <h3 class="text-lg font-bold mb-2 text-yellow-400">Code Inspection</h3>
                            <p class="text-3xl text-yellow-500 font-black" id="code-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-purple-500">
                            <h3 class="text-lg font-bold mb-2 text-purple-400">Right-Click Attempts</h3>
                            <p class="text-3xl text-purple-500 font-black" id="rightclick-attacks">0</p>
                        </div>
                    </div>
                    
                    <!-- Live Attack Feed -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold text-red-400">🚨 Live Attack Monitor</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-red-500">MONITORING</span>
                            </div>
                        </div>
                        <div id="attack-feed" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No attack attempts detected</p>
                        </div>
                    </div>
                    
                    <!-- Attack Details Table -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Attack Attempt Details</h3>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left">
                                <thead>
                                    <tr class="border-b border-gray-700">
                                        <th class="pb-3 font-bold">Time</th>
                                        <th class="pb-3 font-bold">Attack Type</th>
                                        <th class="pb-3 font-bold">Details</th>
                                        <th class="pb-3 font-bold">Location</th>
                                        <th class="pb-3 font-bold">User Agent</th>
                                        <th class="pb-3 font-bold">Severity</th>
                                    </tr>
                                </thead>
                                <tbody id="attack-details-table">
                                    <!-- Attack details will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                    
                    <!-- Attack Response Actions -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6 text-red-400">🛡️ Security Response</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="clearAttackLogs()" class="bg-red-600 hover:bg-red-700 text-white py-3 px-4 rounded-lg font-bold">
                                🗑️ Clear Attack Logs
                            </button>
                            <button onclick="exportAttackData()" class="bg-orange-600 hover:bg-orange-700 text-white py-3 px-4 rounded-lg font-bold">
                                📊 Export Attack Data
                            </button>
                            <button onclick="blockSuspiciousIPs()" class="bg-purple-600 hover:bg-purple-700 text-white py-3 px-4 rounded-lg font-bold">
                                🚫 Block Suspicious IPs
                            </button>
                        </div>
                        
                        <div class="mt-6 p-4 bg-red-900/30 border border-red-500/30 rounded-lg">
                            <h4 class="text-red-400 font-bold mb-2">🔒 Security Status</h4>
                            <p class="text-sm text-red-300">All code inspection attempts are being monitored and logged. Attackers will be warned and their activities recorded.</p>
                            <p class="text-xs text-gray-400 mt-2">Last security scan: <span id="last-security-scan">Just now</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Admin Panel -->
    <section id="admin" class="section py-16 px-4">
        <div class="max-w-7xl mx-auto">
            <h2 class="text-4xl font-black mb-8">ADMIN DASHBOARD</h2>
            
            <!-- Admin Navigation -->
            <div class="flex flex-wrap gap-2 mb-8">
                <button onclick="showAdminTab('overview')" class="admin-tab-btn active bg-orange-500 text-white px-4 py-2 rounded-lg font-medium">Overview</button>
                <button onclick="showAdminTab('security')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Security</button>
                <button onclick="showAdminTab('live-activity')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Live Activity</button>
                <button onclick="showAdminTab('products')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Products</button>
                <button onclick="showAdminTab('users')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Users</button>
                <button onclick="showAdminTab('payments')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Payments</button>
                <button onclick="showAdminTab('customization')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Customization</button>
                <button onclick="showAdminTab('content')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Content</button>
                <button onclick="showAdminTab('customer-service')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">Customer Service</button>
                <button onclick="showAdminTab('attack-monitor')" class="admin-tab-btn bg-gray-700 hover:bg-gray-600 px-4 py-2 rounded-lg font-medium">🚨 Attack Monitor</button>
            </div>
            
            <!-- Security Tab -->
            <div id="admin-security" class="admin-tab">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- Security Status -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Security Status</h3>
                            <div class="flex items-center space-x-2">
                                <div id="security-indicator" class="w-4 h-4 bg-green-500 rounded-full animate-pulse"></div>
                                <span id="security-status" class="text-sm text-green-500 font-medium">SECURE</span>
                            </div>
                        </div>
                        
                        <div class="space-y-4">
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <span>Code Integrity</span>
                                <span id="code-integrity" class="text-green-500">✓ SAFE</span>
                            </div>
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <span>Authentication System</span>
                                <span id="auth-status" class="text-green-500">✓ SECURE</span>
                            </div>
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <span>Admin Access</span>
                                <span id="admin-access" class="text-green-500">✓ PROTECTED</span>
                            </div>
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <span>Data Encryption</span>
                                <span id="data-encryption" class="text-green-500">✓ ACTIVE</span>
                            </div>
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <span>Intrusion Detection</span>
                                <span id="intrusion-detection" class="text-green-500">✓ MONITORING</span>
                            </div>
                        </div>
                        
                        <div class="mt-6 p-4 bg-green-900/30 border border-green-500/30 rounded-lg">
                            <h4 class="text-green-400 font-bold mb-2">🛡️ System Protected</h4>
                            <p class="text-sm text-green-300">All security measures are active. No threats detected.</p>
                            <p class="text-xs text-gray-400 mt-2">Last scan: <span id="last-scan">Just now</span></p>
                        </div>
                    </div>
                    
                    <!-- Security Logs -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Security Logs</h3>
                        <div id="security-logs" class="space-y-3 max-h-96 overflow-y-auto">
                            <!-- Security logs will be populated here -->
                        </div>
                    </div>
                </div>
                
                <!-- Live Security Monitoring -->
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mt-8">
                    <!-- Real-time Security Graph -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Live Security Monitoring</h3>
                        <div class="mb-4">
                            <canvas id="securityChart" width="400" height="200"></canvas>
                        </div>
                        <div class="grid grid-cols-3 gap-4 text-center">
                            <div>
                                <p class="text-2xl font-bold text-green-500" id="security-score">98%</p>
                                <p class="text-xs text-gray-400">Security Score</p>
                            </div>
                            <div>
                                <p class="text-2xl font-bold text-blue-500" id="active-scans">24</p>
                                <p class="text-xs text-gray-400">Active Scans</p>
                            </div>
                            <div>
                                <p class="text-2xl font-bold text-orange-500" id="blocked-threats">0</p>
                                <p class="text-xs text-gray-400">Blocked Today</p>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Threat Detection -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Threat Detection Status</h3>
                        <div class="space-y-4">
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <div class="flex items-center space-x-3">
                                    <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                                    <span>Code Integrity</span>
                                </div>
                                <span class="text-green-500 text-sm">SECURE</span>
                            </div>
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <div class="flex items-center space-x-3">
                                    <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                                    <span>Access Control</span>
                                </div>
                                <span class="text-green-500 text-sm">PROTECTED</span>
                            </div>
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <div class="flex items-center space-x-3">
                                    <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                                    <span>Network Monitor</span>
                                </div>
                                <span class="text-green-500 text-sm">ACTIVE</span>
                            </div>
                            <div class="flex justify-between items-center p-3 bg-gray-800 rounded-lg">
                                <div class="flex items-center space-x-3">
                                    <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                                    <span>Data Encryption</span>
                                </div>
                                <span class="text-green-500 text-sm">ENABLED</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Overview Tab -->
            <div id="admin-overview" class="admin-tab active">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
                    <div class="product-card rounded-xl p-6 text-center">
                        <h3 class="text-lg font-bold mb-2">Total Products</h3>
                        <p class="text-3xl text-orange-500 font-black" id="total-products">12</p>
                    </div>
                    <div class="product-card rounded-xl p-6 text-center">
                        <h3 class="text-lg font-bold mb-2">Total Users</h3>
                        <p class="text-3xl text-orange-500 font-black" id="total-users">0</p>
                    </div>
                    <div class="product-card rounded-xl p-6 text-center">
                        <h3 class="text-lg font-bold mb-2">Total Orders</h3>
                        <p class="text-3xl text-orange-500 font-black" id="total-orders">0</p>
                    </div>
                    <div class="product-card rounded-xl p-6 text-center">
                        <h3 class="text-lg font-bold mb-2">Revenue</h3>
                        <p class="text-3xl text-green-500 font-black" id="total-revenue">$0</p>
                    </div>
                </div>
                
                <!-- Sales Chart -->
                <div class="product-card rounded-xl p-6 mb-8">
                    <h3 class="text-2xl font-bold mb-6">Sales Analytics</h3>
                    <canvas id="salesChart" width="400" height="200"></canvas>
                </div>
            </div>
            
            <!-- Live Activity Tab -->
            <div id="admin-live-activity" class="admin-tab">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- Live Activity Feed -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Live Activity Feed</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-green-500">Live</span>
                            </div>
                        </div>
                        <div id="activity-feed" class="space-y-3 max-h-96 overflow-y-auto">
                            <!-- Activities will be populated here -->
                        </div>
                    </div>
                    
                    <!-- Real-time Charts -->
                    <div class="space-y-6">
                        <div class="product-card rounded-xl p-6">
                            <h3 class="text-xl font-bold mb-4">Active Users</h3>
                            <canvas id="activeUsersChart" width="300" height="150"></canvas>
                        </div>
                        <div class="product-card rounded-xl p-6">
                            <h3 class="text-xl font-bold mb-4">Page Views</h3>
                            <canvas id="pageViewsChart" width="300" height="150"></canvas>
                        </div>
                    </div>
                </div>
                
                <!-- User Activity Table -->
                <div class="product-card rounded-xl p-6 mt-8">
                    <h3 class="text-2xl font-bold mb-6">User Activity Monitor</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left">
                            <thead>
                                <tr class="border-b border-gray-700">
                                    <th class="pb-3 font-bold">User</th>
                                    <th class="pb-3 font-bold">Action</th>
                                    <th class="pb-3 font-bold">Page</th>
                                    <th class="pb-3 font-bold">Time</th>
                                    <th class="pb-3 font-bold">Location</th>
                                    <th class="pb-3 font-bold">Status</th>
                                </tr>
                            </thead>
                            <tbody id="activity-table">
                                <!-- Activity rows will be populated here -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            
            <!-- Products Tab -->
            <div id="admin-products" class="admin-tab">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- Add Product -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">ADD NEW PRODUCT</h3>
                        <form id="add-product-form" class="space-y-4">
                            <input type="text" id="product-name" placeholder="Product Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                            <input type="number" id="product-price" placeholder="Price" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                            <select id="product-category" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                                <option value="">Select Category</option>
                                <option value="tees">Tees</option>
                                <option value="hoodies">Hoodies</option>
                                <option value="bottoms">Bottoms</option>
                                <option value="accessories">Accessories</option>
                            </select>
                            <textarea id="product-description" placeholder="Product Description" rows="3" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                            
                            <!-- Product Image Upload -->
                            <div>
                                <label class="block text-sm font-medium mb-2">Product Images</label>
                                <div class="space-y-2">
                                    <input type="file" id="product-image-1" accept="image/*" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:bg-orange-500 file:text-white hover:file:bg-orange-600">
                                    <input type="file" id="product-image-2" accept="image/*" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:bg-orange-500 file:text-white hover:file:bg-orange-600">
                                    <input type="file" id="product-image-3" accept="image/*" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:bg-orange-500 file:text-white hover:file:bg-orange-600">
                                </div>
                                <p class="text-xs text-gray-400 mt-1">Upload up to 3 product images (JPG, PNG, WebP)</p>
                            </div>
                            
                            <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                ADD PRODUCT
                            </button>
                        </form>
                    </div>
                    
                    <!-- Product Management -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">MANAGE PRODUCTS</h3>
                        <div id="product-management" class="space-y-3 max-h-96 overflow-y-auto">
                            <!-- Products will be listed here -->
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Users Tab -->
            <div id="admin-users" class="admin-tab">
                <div class="product-card rounded-xl p-6">
                    <h3 class="text-2xl font-bold mb-6">USER MANAGEMENT</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left">
                            <thead>
                                <tr class="border-b border-gray-700">
                                    <th class="pb-3 font-bold">Username</th>
                                    <th class="pb-3 font-bold">Email</th>
                                    <th class="pb-3 font-bold">Role</th>
                                    <th class="pb-3 font-bold">Joined</th>
                                    <th class="pb-3 font-bold">Status</th>
                                    <th class="pb-3 font-bold">Actions</th>
                                </tr>
                            </thead>
                            <tbody id="users-table">
                                <!-- Users will be populated here -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            
            <!-- Customization Tab -->
            <div id="admin-customization" class="admin-tab">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- Background Customization -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Background Customization</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="block text-sm font-medium mb-2">Background Style</label>
                                <select id="bg-style" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none">
                                    <option value="gradient">Gradient (Default)</option>
                                    <option value="solid">Solid Color</option>
                                    <option value="pattern">Pattern</option>
                                    <option value="image">Custom Image</option>
                                </select>
                            </div>
                            
                            <div id="color-options">
                                <label class="block text-sm font-medium mb-2">Primary Color</label>
                                <div class="flex space-x-2 mb-4">
                                    <input type="color" id="primary-color" value="#1a1a1a" class="w-12 h-12 rounded border-2 border-gray-600">
                                    <input type="color" id="secondary-color" value="#2d2d2d" class="w-12 h-12 rounded border-2 border-gray-600">
                                </div>
                            </div>
                            
                            <div id="pattern-options" class="hidden">
                                <label class="block text-sm font-medium mb-2">Pattern Type</label>
                                <select id="pattern-type" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none">
                                    <option value="dots">Dots</option>
                                    <option value="lines">Lines</option>
                                    <option value="grid">Grid</option>
                                    <option value="waves">Waves</option>
                                </select>
                            </div>
                            
                            <div id="image-options" class="hidden">
                                <label class="block text-sm font-medium mb-2">Background Images</label>
                                <div class="space-y-3">
                                    <div>
                                        <input type="file" id="bg-image-1" accept="image/*" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:bg-orange-500 file:text-white hover:file:bg-orange-600">
                                        <p class="text-xs text-gray-400 mt-1">Primary background image</p>
                                    </div>
                                    <div>
                                        <input type="file" id="bg-image-2" accept="image/*" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:bg-orange-500 file:text-white hover:file:bg-orange-600">
                                        <p class="text-xs text-gray-400 mt-1">Secondary image (optional)</p>
                                    </div>
                                    <div>
                                        <input type="file" id="bg-image-3" accept="image/*" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:bg-orange-500 file:text-white hover:file:bg-orange-600">
                                        <p class="text-xs text-gray-400 mt-1">Third image (optional)</p>
                                    </div>
                                </div>
                                <div class="mt-4">
                                    <label class="flex items-center space-x-2">
                                        <input type="checkbox" id="enable-slideshow" class="rounded">
                                        <span class="text-sm">Enable slideshow (auto-rotate every 10 seconds)</span>
                                    </label>
                                </div>
                                <div class="mt-4 p-3 bg-blue-900/30 border border-blue-500/30 rounded-lg">
                                    <p class="text-blue-400 text-sm">💡 <strong>Tip:</strong> Upload high-quality images (1920x1080 or larger) for best results. Images will be automatically optimized for web display.</p>
                                </div>
                            </div>
                            
                            <button onclick="applyBackgroundChanges()" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                APPLY CHANGES
                            </button>
                            
                            <button onclick="resetBackground()" class="w-full bg-gray-700 hover:bg-gray-600 text-white py-2 rounded-lg font-medium transition-all">
                                RESET TO DEFAULT
                            </button>
                        </div>
                    </div>
                    
                    <!-- Theme Presets -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Theme Presets</h3>
                        <div class="grid grid-cols-2 gap-4">
                            <button onclick="applyTheme('dark')" class="p-4 bg-gray-900 border-2 border-gray-700 rounded-lg hover:border-orange-500 transition-colors">
                                <div class="w-full h-16 bg-gradient-to-r from-gray-800 to-gray-900 rounded mb-2"></div>
                                <p class="text-sm font-medium">Dark Mode</p>
                            </button>
                            <button onclick="applyTheme('blue')" class="p-4 bg-gray-900 border-2 border-gray-700 rounded-lg hover:border-orange-500 transition-colors">
                                <div class="w-full h-16 bg-gradient-to-r from-blue-800 to-blue-900 rounded mb-2"></div>
                                <p class="text-sm font-medium">Ocean Blue</p>
                            </button>
                            <button onclick="applyTheme('purple')" class="p-4 bg-gray-900 border-2 border-gray-700 rounded-lg hover:border-orange-500 transition-colors">
                                <div class="w-full h-16 bg-gradient-to-r from-purple-800 to-purple-900 rounded mb-2"></div>
                                <p class="text-sm font-medium">Royal Purple</p>
                            </button>
                            <button onclick="applyTheme('green')" class="p-4 bg-gray-900 border-2 border-gray-700 rounded-lg hover:border-orange-500 transition-colors">
                                <div class="w-full h-16 bg-gradient-to-r from-green-800 to-green-900 rounded mb-2"></div>
                                <p class="text-sm font-medium">Forest Green</p>
                            </button>
                        </div>
                        
                        <div class="mt-6 p-4 bg-gray-800 rounded-lg">
                            <h4 class="font-bold mb-2">Current Theme</h4>
                            <p class="text-sm text-gray-400" id="current-theme">Default Dark Theme</p>
                            <p class="text-xs text-gray-500 mt-1">Last modified: <span id="theme-modified">Never</span></p>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Content Management Tab -->
            <div id="admin-content" class="admin-tab">
                <div class="space-y-8">
                    <!-- About Section Editor -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Edit About Section</h3>
                        <form id="about-form" class="space-y-4">
                            <div>
                                <label class="block text-sm font-medium mb-2">Company Name</label>
                                <input type="text" id="company-name" value="HUSTLE SUPPLY" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium mb-2">Tagline</label>
                                <input type="text" id="company-tagline" value="Crafted for the Grind" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium mb-2">Main Description</label>
                                <textarea id="main-description" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none">Born from the streets, crafted for the grind. HUSTLE SUPPLY represents more than just clothing – it's a mindset.</textarea>
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium mb-2">Company Story</label>
                                <textarea id="company-story" rows="6" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none">Founded in 2024, we believe that success isn't given, it's earned. Every thread, every stitch, every design tells the story of those who refuse to settle. Our premium streetwear is designed for the relentless, the ambitious, and the unstoppable.</textarea>
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium mb-2">Mission Statement</label>
                                <textarea id="mission-statement" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none">To empower the next generation of entrepreneurs, creators, and dreamers with clothing that reflects their ambition. We're not just selling apparel – we're building a movement of individuals who understand that success is a choice, and every day is an opportunity to level up.</textarea>
                            </div>
                            
                            <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                UPDATE ABOUT SECTION
                            </button>
                        </form>
                    </div>
                    
                    <!-- Contact Information Editor -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Edit Contact Information</h3>
                        <form id="contact-form" class="space-y-4">
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                                <div>
                                    <label class="block text-sm font-medium mb-2">Email</label>
                                    <input type="email" id="contact-email" value="hello@hustlesupply.com" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                                </div>
                                <div>
                                    <label class="block text-sm font-medium mb-2">Phone</label>
                                    <input type="tel" id="contact-phone" value="+1 (555) 123-HUSTLE" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                                </div>
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium mb-2">Address</label>
                                <input type="text" id="contact-address" value="123 Grind Street, Hustle City, HC 12345" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium mb-2">Business Hours</label>
                                <input type="text" id="contact-hours" value="Mon-Fri: 9AM-6PM PST" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                            </div>
                            
                            <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                UPDATE CONTACT INFO
                            </button>
                        </form>
                    </div>
                </div>
            </div>
            
            <!-- Payments Tab -->
            <div id="admin-payments" class="admin-tab">
                <div class="space-y-8">
                    <!-- Payment Receiver Methods -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Payment Receiver Methods</h3>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                            <!-- Add Payment Method -->
                            <div>
                                <h4 class="text-lg font-bold mb-4">Add Payment Receiver</h4>
                                <form id="payment-receiver-form" class="space-y-4">
                                    <select id="payment-type" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                                        <option value="">Select Payment Type</option>
                                        <option value="bank">Bank Account</option>
                                        <option value="paypal">PayPal</option>
                                        <option value="stripe">Stripe</option>
                                        <option value="crypto">Cryptocurrency</option>
                                        <option value="mobile-money">Mobile Money</option>
                                        <option value="digital-wallet">Digital Wallet</option>
                                    </select>
                                    
                                    <input type="text" id="receiver-name" placeholder="Account/Receiver Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    
                                    <input type="text" id="receiver-details" placeholder="Account Number/Address/Email" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    
                                    <select id="receiver-currency" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                                        <option value="">Select Currency</option>
                                        <!-- Will be populated with all world currencies -->
                                    </select>
                                    
                                    <input type="text" id="receiver-country" placeholder="Country" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    
                                    <textarea id="receiver-notes" placeholder="Additional Notes (Optional)" rows="2" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none"></textarea>
                                    
                                    <div class="flex items-center space-x-2">
                                        <input type="checkbox" id="auto-process" class="rounded">
                                        <label for="auto-process" class="text-sm">Auto-process payments to this receiver</label>
                                    </div>
                                    
                                    <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                        ADD PAYMENT RECEIVER
                                    </button>
                                </form>
                            </div>
                            
                            <!-- Active Payment Receivers -->
                            <div>
                                <h4 class="text-lg font-bold mb-4">Active Payment Receivers</h4>
                                <div id="payment-receivers-list" class="space-y-3 max-h-96 overflow-y-auto">
                                    <p class="text-gray-400 text-center py-8">No payment receivers configured</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Payment Authorization Queue -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Payment Authorization Queue</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-yellow-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-yellow-500" id="pending-payments">0 Pending</span>
                            </div>
                        </div>
                        <div id="payment-queue" class="space-y-4">
                            <p class="text-gray-400 text-center py-8">No pending payments</p>
                        </div>
                    </div>
                    
                    <!-- Payment History -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Payment History</h3>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left">
                                <thead>
                                    <tr class="border-b border-gray-700">
                                        <th class="pb-3 font-bold">Order ID</th>
                                        <th class="pb-3 font-bold">Customer</th>
                                        <th class="pb-3 font-bold">Amount</th>
                                        <th class="pb-3 font-bold">Method</th>
                                        <th class="pb-3 font-bold">Receiver</th>
                                        <th class="pb-3 font-bold">Status</th>
                                        <th class="pb-3 font-bold">Date</th>
                                    </tr>
                                </thead>
                                <tbody id="payment-history">
                                    <!-- Payment history will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Customer Service Tab -->
            <div id="admin-customer-service" class="admin-tab">
                <div class="space-y-8">
                    <!-- Customer Messages -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold">Customer Messages</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-blue-500" id="unread-messages">0 Unread</span>
                            </div>
                        </div>
                        <div id="customer-messages" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No customer messages</p>
                        </div>
                    </div>
                    
                    <!-- Product Reviews & Ratings -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Product Reviews & Ratings</h3>
                        <div id="product-reviews" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No product reviews yet</p>
                        </div>
                    </div>
                    
                    <!-- Quick Response Templates -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Quick Response Templates</h3>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                            <div>
                                <h4 class="text-lg font-bold mb-4">Add Template</h4>
                                <form id="response-template-form" class="space-y-4">
                                    <input type="text" id="template-name" placeholder="Template Name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                    <textarea id="template-content" placeholder="Template Content" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                                    <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                                        ADD TEMPLATE
                                    </button>
                                </form>
                            </div>
                            <div>
                                <h4 class="text-lg font-bold mb-4">Saved Templates</h4>
                                <div id="response-templates" class="space-y-2 max-h-64 overflow-y-auto">
                                    <p class="text-gray-400 text-center py-8">No templates saved</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Attack Monitor Tab -->
            <div id="admin-attack-monitor" class="admin-tab">
                <div class="space-y-8">
                    <!-- Attack Statistics -->
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-red-500">
                            <h3 class="text-lg font-bold mb-2 text-red-400">Total Attacks</h3>
                            <p class="text-3xl text-red-500 font-black" id="total-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-orange-500">
                            <h3 class="text-lg font-bold mb-2 text-orange-400">Today's Attacks</h3>
                            <p class="text-3xl text-orange-500 font-black" id="today-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-yellow-500">
                            <h3 class="text-lg font-bold mb-2 text-yellow-400">Code Inspection</h3>
                            <p class="text-3xl text-yellow-500 font-black" id="code-attacks">0</p>
                        </div>
                        <div class="product-card rounded-xl p-6 text-center border-l-4 border-purple-500">
                            <h3 class="text-lg font-bold mb-2 text-purple-400">Right-Click Attempts</h3>
                            <p class="text-3xl text-purple-500 font-black" id="rightclick-attacks">0</p>
                        </div>
                    </div>
                    
                    <!-- Live Attack Feed -->
                    <div class="product-card rounded-xl p-6">
                        <div class="flex justify-between items-center mb-6">
                            <h3 class="text-2xl font-bold text-red-400">🚨 Live Attack Monitor</h3>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-red-500">MONITORING</span>
                            </div>
                        </div>
                        <div id="attack-feed" class="space-y-4 max-h-96 overflow-y-auto">
                            <p class="text-gray-400 text-center py-8">No attack attempts detected</p>
                        </div>
                    </div>
                    
                    <!-- Attack Details Table -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6">Attack Attempt Details</h3>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left">
                                <thead>
                                    <tr class="border-b border-gray-700">
                                        <th class="pb-3 font-bold">Time</th>
                                        <th class="pb-3 font-bold">Attack Type</th>
                                        <th class="pb-3 font-bold">Details</th>
                                        <th class="pb-3 font-bold">Location</th>
                                        <th class="pb-3 font-bold">User Agent</th>
                                        <th class="pb-3 font-bold">Severity</th>
                                    </tr>
                                </thead>
                                <tbody id="attack-details-table">
                                    <!-- Attack details will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                    
                    <!-- Attack Response Actions -->
                    <div class="product-card rounded-xl p-6">
                        <h3 class="text-2xl font-bold mb-6 text-red-400">🛡️ Security Response</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="clearAttackLogs()" class="bg-red-600 hover:bg-red-700 text-white py-3 px-4 rounded-lg font-bold">
                                🗑️ Clear Attack Logs
                            </button>
                            <button onclick="exportAttackData()" class="bg-orange-600 hover:bg-orange-700 text-white py-3 px-4 rounded-lg font-bold">
                                📊 Export Attack Data
                            </button>
                            <button onclick="blockSuspiciousIPs()" class="bg-purple-600 hover:bg-purple-700 text-white py-3 px-4 rounded-lg font-bold">
                                🚫 Block Suspicious IPs
                            </button>
                        </div>
                        
                        <div class="mt-6 p-4 bg-red-900/30 border border-red-500/30 rounded-lg">
                            <h4 class="text-red-400 font-bold mb-2">🔒 Security Status</h4>
                            <p class="text-sm text-red-300">All code inspection attempts are being monitored and logged. Attackers will be warned and their activities recorded.</p>
                            <p class="text-xs text-gray-400 mt-2">Last security scan: <span id="last-security-scan">Just now</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Login Modal -->
    <div id="login-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-lg w-full mx-4">
            <div class="text-center mb-6">
                <h3 class="text-3xl font-bold mb-4 bg-gradient-to-r from-orange-500 to-red-500 bg-clip-text text-transparent">🔥 HUSTLE LOGIN 💎</h3>
                <p class="text-gray-400 text-sm">Choose your country and join the grind!</p>
            </div>
            
            <form id="login-form" class="space-y-4">
                <!-- Country Selection -->
                <div>
                    <label class="block text-sm font-medium mb-2 text-gray-300">Select Your Country</label>
                    <select id="login-country" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                        <option value="">🌍 Choose your country...</option>
                        <option value="US">🇺🇸 United States</option>
                        <option value="GB">🇬🇧 United Kingdom</option>
                        <option value="CA">🇨🇦 Canada</option>
                        <option value="AU">🇦🇺 Australia</option>
                        <option value="DE">🇩🇪 Germany</option>
                        <option value="FR">🇫🇷 France</option>
                        <option value="ES">🇪🇸 Spain</option>
                        <option value="IT">🇮🇹 Italy</option>
                        <option value="NL">🇳🇱 Netherlands</option>
                        <option value="SE">🇸🇪 Sweden</option>
                        <option value="NO">🇳🇴 Norway</option>
                        <option value="DK">🇩🇰 Denmark</option>
                        <option value="FI">🇫🇮 Finland</option>
                        <option value="CH">🇨🇭 Switzerland</option>
                        <option value="AT">🇦🇹 Austria</option>
                        <option value="BE">🇧🇪 Belgium</option>
                        <option value="IE">🇮🇪 Ireland</option>
                        <option value="PT">🇵🇹 Portugal</option>
                        <option value="GR">🇬🇷 Greece</option>
                        <option value="PL">🇵🇱 Poland</option>
                        <option value="CZ">🇨🇿 Czech Republic</option>
                        <option value="HU">🇭🇺 Hungary</option>
                        <option value="RO">🇷🇴 Romania</option>
                        <option value="BG">🇧🇬 Bulgaria</option>
                        <option value="HR">🇭🇷 Croatia</option>
                        <option value="SI">🇸🇮 Slovenia</option>
                        <option value="SK">🇸🇰 Slovakia</option>
                        <option value="LT">🇱🇹 Lithuania</option>
                        <option value="LV">🇱🇻 Latvia</option>
                        <option value="EE">🇪🇪 Estonia</option>
                        <option value="JP">🇯🇵 Japan</option>
                        <option value="KR">🇰🇷 South Korea</option>
                        <option value="CN">🇨🇳 China</option>
                        <option value="IN">🇮🇳 India</option>
                        <option value="SG">🇸🇬 Singapore</option>
                        <option value="HK">🇭🇰 Hong Kong</option>
                        <option value="TW">🇹🇼 Taiwan</option>
                        <option value="TH">🇹🇭 Thailand</option>
                        <option value="MY">🇲🇾 Malaysia</option>
                        <option value="ID">🇮🇩 Indonesia</option>
                        <option value="PH">🇵🇭 Philippines</option>
                        <option value="VN">🇻🇳 Vietnam</option>
                        <option value="BD">🇧🇩 Bangladesh</option>
                        <option value="PK">🇵🇰 Pakistan</option>
                        <option value="LK">🇱🇰 Sri Lanka</option>
                        <option value="NP">🇳🇵 Nepal</option>
                        <option value="MM">🇲🇲 Myanmar</option>
                        <option value="KH">🇰🇭 Cambodia</option>
                        <option value="LA">🇱🇦 Laos</option>
                        <option value="BN">🇧🇳 Brunei</option>
                        <option value="MV">🇲🇻 Maldives</option>
                        <option value="BT">🇧🇹 Bhutan</option>
                        <option value="NG">🇳🇬 Nigeria</option>
                        <option value="ZA">🇿🇦 South Africa</option>
                        <option value="EG">🇪🇬 Egypt</option>
                        <option value="KE">🇰🇪 Kenya</option>
                        <option value="GH">🇬🇭 Ghana</option>
                        <option value="ET">🇪🇹 Ethiopia</option>
                        <option value="UG">🇺🇬 Uganda</option>
                        <option value="TZ">🇹🇿 Tanzania</option>
                        <option value="RW">🇷🇼 Rwanda</option>
                        <option value="SN">🇸🇳 Senegal</option>
                        <option value="CI">🇨🇮 Ivory Coast</option>
                        <option value="CM">🇨🇲 Cameroon</option>
                        <option value="BF">🇧🇫 Burkina Faso</option>
                        <option value="ML">🇲🇱 Mali</option>
                        <option value="NE">🇳🇪 Niger</option>
                        <option value="TD">🇹🇩 Chad</option>
                        <option value="SD">🇸🇩 Sudan</option>
                        <option value="LY">🇱🇾 Libya</option>
                        <option value="TN">🇹🇳 Tunisia</option>
                        <option value="DZ">🇩🇿 Algeria</option>
                        <option value="MA">🇲🇦 Morocco</option>
                        <option value="MX">🇲🇽 Mexico</option>
                        <option value="BR">🇧🇷 Brazil</option>
                        <option value="AR">🇦🇷 Argentina</option>
                        <option value="CL">🇨🇱 Chile</option>
                        <option value="CO">🇨🇴 Colombia</option>
                        <option value="PE">🇵🇪 Peru</option>
                        <option value="VE">🇻🇪 Venezuela</option>
                        <option value="EC">🇪🇨 Ecuador</option>
                        <option value="BO">🇧🇴 Bolivia</option>
                        <option value="PY">🇵🇾 Paraguay</option>
                        <option value="UY">🇺🇾 Uruguay</option>
                        <option value="GY">🇬🇾 Guyana</option>
                        <option value="SR">🇸🇷 Suriname</option>
                        <option value="GF">🇬🇫 French Guiana</option>
                        <option value="CR">🇨🇷 Costa Rica</option>
                        <option value="PA">🇵🇦 Panama</option>
                        <option value="NI">🇳🇮 Nicaragua</option>
                        <option value="HN">🇭🇳 Honduras</option>
                        <option value="GT">🇬🇹 Guatemala</option>
                        <option value="BZ">🇧🇿 Belize</option>
                        <option value="SV">🇸🇻 El Salvador</option>
                        <option value="CU">🇨🇺 Cuba</option>
                        <option value="JM">🇯🇲 Jamaica</option>
                        <option value="HT">🇭🇹 Haiti</option>
                        <option value="DO">🇩🇴 Dominican Republic</option>
                        <option value="PR">🇵🇷 Puerto Rico</option>
                        <option value="TT">🇹🇹 Trinidad and Tobago</option>
                        <option value="BB">🇧🇧 Barbados</option>
                        <option value="BS">🇧🇸 Bahamas</option>
                        <option value="RU">🇷🇺 Russia</option>
                        <option value="UA">🇺🇦 Ukraine</option>
                        <option value="BY">🇧🇾 Belarus</option>
                        <option value="MD">🇲🇩 Moldova</option>
                        <option value="GE">🇬🇪 Georgia</option>
                        <option value="AM">🇦🇲 Armenia</option>
                        <option value="AZ">🇦🇿 Azerbaijan</option>
                        <option value="KZ">🇰🇿 Kazakhstan</option>
                        <option value="UZ">🇺🇿 Uzbekistan</option>
                        <option value="TM">🇹🇲 Turkmenistan</option>
                        <option value="KG">🇰🇬 Kyrgyzstan</option>
                        <option value="TJ">🇹🇯 Tajikistan</option>
                        <option value="MN">🇲🇳 Mongolia</option>
                        <option value="AF">🇦🇫 Afghanistan</option>
                        <option value="IR">🇮🇷 Iran</option>
                        <option value="IQ">🇮🇶 Iraq</option>
                        <option value="SY">🇸🇾 Syria</option>
                        <option value="LB">🇱🇧 Lebanon</option>
                        <option value="JO">🇯🇴 Jordan</option>
                        <option value="IL">🇮🇱 Israel</option>
                        <option value="PS">🇵🇸 Palestine</option>
                        <option value="SA">🇸🇦 Saudi Arabia</option>
                        <option value="AE">🇦🇪 UAE</option>
                        <option value="QA">🇶🇦 Qatar</option>
                        <option value="BH">🇧🇭 Bahrain</option>
                        <option value="KW">🇰🇼 Kuwait</option>
                        <option value="OM">🇴🇲 Oman</option>
                        <option value="YE">🇾🇪 Yemen</option>
                        <option value="TR">🇹🇷 Turkey</option>
                        <option value="CY">🇨🇾 Cyprus</option>
                        <option value="MT">🇲🇹 Malta</option>
                        <option value="IS">🇮🇸 Iceland</option>
                        <option value="GL">🇬🇱 Greenland</option>
                        <option value="FO">🇫🇴 Faroe Islands</option>
                        <option value="NZ">🇳🇿 New Zealand</option>
                        <option value="FJ">🇫🇯 Fiji</option>
                        <option value="PG">🇵🇬 Papua New Guinea</option>
                        <option value="SB">🇸🇧 Solomon Islands</option>
                        <option value="VU">🇻🇺 Vanuatu</option>
                        <option value="NC">🇳🇨 New Caledonia</option>
                        <option value="PF">🇵🇫 French Polynesia</option>
                        <option value="WS">🇼🇸 Samoa</option>
                        <option value="TO">🇹🇴 Tonga</option>
                        <option value="KI">🇰🇮 Kiribati</option>
                        <option value="TV">🇹🇻 Tuvalu</option>
                        <option value="NR">🇳🇷 Nauru</option>
                        <option value="PW">🇵🇼 Palau</option>
                        <option value="FM">🇫🇲 Micronesia</option>
                        <option value="MH">🇲🇭 Marshall Islands</option>
                    </select>
                </div>
                
                <input type="text" id="login-username" placeholder="👤 Username" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                <input type="email" id="login-email" placeholder="📧 Email" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                <input type="password" id="login-password" placeholder="🔒 Password" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                
                <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all transform hover:scale-105">
                    🚀 START THE GRIND 🚀
                </button>
            </form>
            <p class="text-center text-gray-400 mt-4">
                Don't have an account? 
                <button onclick="showModal('signup')" class="text-orange-500 hover:text-orange-400">Sign up</button>
            </p>
            <p class="text-center text-gray-400 mt-2">
                <button onclick="showModal('reset')" class="text-orange-500 hover:text-orange-400 text-sm">Forgot Password?</button>
            </p>
            <button onclick="hideModal('login')" class="absolute top-4 right-4 text-gray-400 hover:text-white">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>
        </div>
    </div>

    <!-- Signup Modal -->
    <div id="signup-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-md w-full mx-4">
            <h3 class="text-2xl font-bold mb-6 text-center">SIGN UP</h3>
            <form id="signup-form" class="space-y-4">
                <input type="text" id="signup-username" placeholder="Username" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                <input type="email" id="signup-email" placeholder="Email" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                <input type="password" id="signup-password" placeholder="Password" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                <input type="password" id="signup-confirm-password" placeholder="Confirm Password" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                    SIGN UP
                </button>
            </form>
            <p class="text-center text-gray-400 mt-4">
                Already have an account? 
                <button onclick="showModal('login')" class="text-orange-500 hover:text-orange-400">Login</button>
            </p>
            <button onclick="hideModal('signup')" class="absolute top-4 right-4 text-gray-400 hover:text-white">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>
        </div>
    </div>

    <!-- Password Reset Modal -->
    <div id="reset-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-md w-full mx-4">
            <h3 class="text-2xl font-bold mb-6 text-center">RESET PASSWORD</h3>
            <form id="reset-form" class="space-y-4">
                <input type="email" id="reset-email" placeholder="Enter your email" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                    SEND RESET LINK
                </button>
            </form>
            <p class="text-center text-gray-400 mt-4">
                Remember your password? 
                <button onclick="showModal('login')" class="text-orange-500 hover:text-orange-400">Login</button>
            </p>
            <button onclick="hideModal('reset')" class="absolute top-4 right-4 text-gray-400 hover:text-white">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>
        </div>
    </div>

    <!-- Profile Modal -->
    <div id="profile-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-md w-full mx-4">
            <h3 class="text-2xl font-bold mb-6 text-center">PROFILE SETTINGS</h3>
            <form id="profile-form" class="space-y-4">
                <!-- Profile Picture Upload -->
                <div class="text-center">
                    <div class="relative inline-block">
                        <img id="profile-preview" src="" alt="Profile Preview" class="w-24 h-24 rounded-full bg-gray-600 mx-auto mb-4 hidden">
                        <div id="profile-placeholder" class="w-24 h-24 rounded-full bg-gradient-to-r from-orange-500 to-red-500 flex items-center justify-center mx-auto mb-4">
                            <span id="profile-initial" class="text-white text-2xl font-bold"></span>
                        </div>
                        <input type="file" id="profile-picture" accept="image/*" class="hidden">
                        <button type="button" onclick="document.getElementById('profile-picture').click()" class="absolute bottom-2 right-2 w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center hover:bg-orange-600 transition-colors">
                            <svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path>
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path>
                            </svg>
                        </button>
                    </div>
                    <p class="text-sm text-gray-400">Click camera icon to upload profile picture</p>
                </div>
                
                <input type="text" id="profile-username" placeholder="Username" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" readonly>
                <input type="email" id="profile-email" placeholder="Email" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                <input type="password" id="profile-new-password" placeholder="New Password (optional)" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                <input type="password" id="profile-confirm-password" placeholder="Confirm New Password" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                
                <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                    UPDATE PROFILE
                </button>
            </form>
            <button onclick="hideModal('profile')" class="absolute top-4 right-4 text-gray-400 hover:text-white">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>
        </div>
    </div>

    <!-- Checkout Modal -->
    <div id="checkout-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-4xl w-full mx-4 max-h-screen overflow-y-auto">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold">CHECKOUT</h3>
                <button onclick="hideModal('checkout')" class="text-gray-400 hover:text-white">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <!-- Shipping Information -->
                <div class="space-y-6">
                    <div>
                        <h4 class="text-xl font-bold mb-4">SHIPPING INFORMATION</h4>
                        <form id="shipping-form" class="space-y-4">
                            <div class="grid grid-cols-2 gap-4">
                                <input type="text" id="first-name" placeholder="First Name" class="bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                <input type="text" id="last-name" placeholder="Last Name" class="bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                            </div>
                            <input type="email" id="checkout-email" placeholder="Email Address" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                            <input type="tel" id="phone" placeholder="Phone Number" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                            <input type="text" id="address" placeholder="Street Address" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                            <div class="grid grid-cols-2 gap-4">
                                <input type="text" id="city" placeholder="City" class="bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                                <input type="text" id="zip-code" placeholder="ZIP Code" class="bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                            </div>
                            <select id="country" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                                <option value="">Select Country</option>
                                <option value="US">United States</option>
                                <option value="CA">Canada</option>
                                <option value="UK">United Kingdom</option>
                                <option value="AU">Australia</option>
                                <option value="DE">Germany</option>
                                <option value="FR">France</option>
                                <option value="JP">Japan</option>
                                <option value="NG">Nigeria</option>
                                <option value="ZA">South Africa</option>
                                <option value="BR">Brazil</option>
                                <option value="IN">India</option>
                                <option value="CN">China</option>
                            </select>
                            <div class="flex items-center space-x-2">
                                <input type="checkbox" id="same-billing" class="rounded">
                                <label for="same-billing" class="text-sm text-gray-300">Billing address same as shipping</label>
                            </div>
                        </form>
                    </div>
                    
                    <!-- Payment Methods -->
                    <div>
                        <h4 class="text-xl font-bold mb-4">PAYMENT METHOD</h4>
                        <div id="payment-methods" class="space-y-3">
                            <!-- Payment methods will be populated based on location -->
                        </div>
                        
                        <!-- Payment Form -->
                        <div id="payment-form" class="mt-6 space-y-4 hidden">
                            <!-- Credit Card Form -->
                            <div id="card-form" class="space-y-4">
                                <input type="text" id="card-number" placeholder="Card Number" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                                <div class="grid grid-cols-2 gap-4">
                                    <input type="text" id="expiry" placeholder="MM/YY" class="bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                                    <input type="text" id="cvv" placeholder="CVV" class="bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                                </div>
                                <input type="text" id="card-name" placeholder="Name on Card" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                            </div>
                            
                            <!-- Bitcoin Form -->
                            <div id="bitcoin-form" class="space-y-4 hidden">
                                <div class="bg-gray-800 rounded-lg p-4">
                                    <p class="text-sm text-gray-300 mb-2">Bitcoin Address:</p>
                                    <p class="font-mono text-orange-500 text-sm break-all">1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa</p>
                                    <p class="text-xs text-gray-400 mt-2">Send exact amount to complete payment</p>
                                </div>
                            </div>
                            
                            <!-- Mobile Payment Form -->
                            <div id="mobile-form" class="space-y-4 hidden">
                                <input type="tel" id="mobile-number" placeholder="Mobile Number" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                                <p class="text-sm text-gray-400">You will receive an SMS with payment instructions</p>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Order Summary -->
                <div class="space-y-6">
                    <div>
                        <h4 class="text-xl font-bold mb-4">ORDER SUMMARY</h4>
                        <div id="checkout-items" class="space-y-3 mb-4">
                            <!-- Cart items will be displayed here -->
                        </div>
                        
                        <div class="border-t border-gray-700 pt-4 space-y-2">
                            <div class="flex justify-between">
                                <span>Subtotal:</span>
                                <span id="checkout-subtotal">$0</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Shipping:</span>
                                <span id="checkout-shipping">$10</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Tax:</span>
                                <span id="checkout-tax">$0</span>
                            </div>
                            <div class="flex justify-between text-xl font-bold border-t border-gray-700 pt-2">
                                <span>Total:</span>
                                <span id="checkout-total">$0</span>
                            </div>
                        </div>
                    </div>
                    
                    <button onclick="processPayment()" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-4 rounded-lg font-bold text-lg hover:from-orange-600 hover:to-red-600 transition-all">
                        COMPLETE ORDER
                    </button>
                    
                    <div class="text-center text-xs text-gray-400">
                        <p>🔒 Secure payment processing</p>
                        <p>All payments require admin authorization</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Product Images Modal -->
    <div id="product-images-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-4xl w-full mx-4 max-h-screen overflow-y-auto">
            <div class="flex justify-between items-center mb-6">
                <h3 id="product-modal-title" class="text-2xl font-bold">Product Images</h3>
                <button onclick="hideModal('product-images')" class="text-gray-400 hover:text-white">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            
            <div id="product-images-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                <!-- Product images will be displayed here -->
            </div>
            
            <div id="product-image-details" class="mt-6 p-4 bg-gray-800 rounded-lg">
                <h4 class="font-bold mb-2">Image Details</h4>
                <div id="selected-image-info" class="text-sm text-gray-400">
                    Click on an image to view details
                </div>
            </div>
        </div>
    </div>

    <!-- Product Rating Modal -->
    <div id="product-rating-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-md w-full mx-4">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold">Rate Product</h3>
                <button onclick="hideModal('product-rating')" class="text-gray-400 hover:text-white">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            
            <form id="product-rating-form" class="space-y-4">
                <div>
                    <h4 id="rating-product-name" class="text-lg font-bold mb-2"></h4>
                    <p class="text-gray-400 text-sm mb-4">Share your experience with this product</p>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Rating</label>
                    <div class="flex space-x-1 mb-2">
                        <button type="button" class="star-rating text-2xl text-gray-400 hover:text-yellow-500" data-rating="1">★</button>
                        <button type="button" class="star-rating text-2xl text-gray-400 hover:text-yellow-500" data-rating="2">★</button>
                        <button type="button" class="star-rating text-2xl text-gray-400 hover:text-yellow-500" data-rating="3">★</button>
                        <button type="button" class="star-rating text-2xl text-gray-400 hover:text-yellow-500" data-rating="4">★</button>
                        <button type="button" class="star-rating text-2xl text-gray-400 hover:text-yellow-500" data-rating="5">★</button>
                    </div>
                    <p id="rating-text" class="text-sm text-gray-400">Click stars to rate</p>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Review Title</label>
                    <input type="text" id="review-title" placeholder="Brief title for your review" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Your Review</label>
                    <textarea id="review-comment" placeholder="Tell others about your experience..." rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                </div>
                
                <div class="flex items-center space-x-2">
                    <input type="checkbox" id="recommend-product" class="rounded">
                    <label for="recommend-product" class="text-sm">I would recommend this product</label>
                </div>
                
                <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                    SUBMIT REVIEW
                </button>
            </form>
        </div>
    </div>

    <!-- Product Request Modal -->
    <div id="product-request-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-md w-full mx-4">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold text-green-400">📦 Product Request</h3>
                <button onclick="hideModal('product-request')" class="text-gray-400 hover:text-white">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            
            <div class="mb-4 p-4 bg-green-900/30 border border-green-500/30 rounded-lg">
                <h4 id="request-product-name" class="font-bold text-green-400 mb-2"></h4>
                <p class="text-green-300 text-sm">Request this product from our admin team! We'll notify you when it becomes available.</p>
            </div>
            
            <form id="product-request-form" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium mb-2">Request Type</label>
                    <select id="request-type" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                        <option value="">Select request type</option>
                        <option value="restock">🔄 Restock Request</option>
                        <option value="size">📏 Different Size</option>
                        <option value="color">🎨 Different Color</option>
                        <option value="variant">✨ Product Variant</option>
                        <option value="custom">🛠️ Custom Design</option>
                        <option value="bulk">📦 Bulk Order</option>
                        <option value="wholesale">🏢 Wholesale Inquiry</option>
                    </select>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Quantity Needed</label>
                    <input type="number" id="request-quantity" placeholder="How many do you need?" min="1" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none" required>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Specific Requirements</label>
                    <textarea id="request-details" placeholder="Describe your specific needs (size, color, design modifications, etc.)" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Budget Range (Optional)</label>
                    <select id="request-budget" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none">
                        <option value="">Select budget range</option>
                        <option value="under-50">💰 Under $50</option>
                        <option value="50-100">💰 $50 - $100</option>
                        <option value="100-250">💰 $100 - $250</option>
                        <option value="250-500">💰 $250 - $500</option>
                        <option value="500-1000">💰 $500 - $1,000</option>
                        <option value="over-1000">💰 Over $1,000</option>
                        <option value="negotiable">🤝 Negotiable</option>
                    </select>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Timeline</label>
                    <select id="request-timeline" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                        <option value="">When do you need this?</option>
                        <option value="asap">🚀 ASAP</option>
                        <option value="1-week">📅 Within 1 week</option>
                        <option value="2-weeks">📅 Within 2 weeks</option>
                        <option value="1-month">📅 Within 1 month</option>
                        <option value="flexible">⏰ Flexible timeline</option>
                    </select>
                </div>
                
                <div class="flex items-center space-x-2">
                    <input type="checkbox" id="notify-availability" class="rounded" checked>
                    <label for="notify-availability" class="text-sm">📧 Notify me when this becomes available</label>
                </div>
                
                <button type="submit" class="w-full bg-gradient-to-r from-green-500 to-green-600 text-white py-3 rounded-lg font-bold hover:from-green-600 hover:to-green-700 transition-all">
                    📦 SEND REQUEST TO ADMIN
                </button>
            </form>
            
            <div class="mt-4 p-3 bg-blue-900/30 border border-blue-500/30 rounded-lg">
                <p class="text-blue-400 text-sm">💡 <strong>Tip:</strong> Our admin team reviews all product requests and will contact you within 24-48 hours with availability and pricing information.</p>
            </div>
        </div>
    </div>

    <!-- Customer Service Modal -->
    <div id="customer-service-modal" class="fixed inset-0 bg-black bg-opacity-50 modal hidden flex items-center justify-center z-50">
        <div class="bg-gray-900 rounded-xl p-8 max-w-md w-full mx-4">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold">Contact Support</h3>
                <button onclick="hideModal('customer-service')" class="text-gray-400 hover:text-white">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            
            <form id="customer-service-form" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium mb-2">Subject</label>
                    <select id="support-subject" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                        <option value="">Select a subject</option>
                        <option value="order-inquiry">Order Inquiry</option>
                        <option value="product-question">Product Question</option>
                        <option value="shipping-issue">Shipping Issue</option>
                        <option value="return-refund">Return/Refund</option>
                        <option value="technical-issue">Technical Issue</option>
                        <option value="general-inquiry">General Inquiry</option>
                        <option value="complaint">Complaint</option>
                        <option value="compliment">Compliment</option>
                    </select>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Order Number (Optional)</label>
                    <input type="text" id="support-order-number" placeholder="Order #12345" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none">
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Message</label>
                    <textarea id="support-message" placeholder="Please describe your inquiry in detail..." rows="5" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:border-orange-500 focus:outline-none resize-none" required></textarea>
                </div>
                
                <div>
                    <label class="block text-sm font-medium mb-2">Priority</label>
                    <select id="support-priority" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-3 text-white focus:border-orange-500 focus:outline-none" required>
                        <option value="low">Low - General inquiry</option>
                        <option value="medium" selected>Medium - Standard request</option>
                        <option value="high">High - Urgent issue</option>
                        <option value="critical">Critical - Emergency</option>
                    </select>
                </div>
                
                <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                    SEND MESSAGE
                </button>
            </form>
        </div>
    </div>

    <!-- Cart Sidebar -->
    <div id="cart-sidebar" class="fixed right-0 top-0 h-full w-96 bg-black border-l border-gray-700 transform translate-x-full transition-transform duration-300 z-50">
        <div class="p-6">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-xl font-bold">Your Cart</h3>
                <button onclick="toggleCart()" class="text-gray-400 hover:text-white">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            
            <div id="cart-items" class="space-y-4 mb-6">
                <p class="text-gray-400 text-center py-8">Your cart is empty</p>
            </div>
            
            <div id="cart-total" class="border-t border-gray-700 pt-4 hidden">
                <div class="flex justify-between items-center mb-4">
                    <span class="text-lg font-bold">Total:</span>
                    <span id="total-amount" class="text-lg font-bold">$0</span>
                </div>
                <button onclick="showCheckout()" class="w-full bg-gradient-to-r from-orange-500 to-red-500 text-white py-3 rounded-lg font-bold hover:from-orange-600 hover:to-red-600 transition-all">
                    CHECKOUT
                </button>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="border-t border-gray-700 py-12 px-4 mt-16">
        <div class="max-w-7xl mx-auto">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                <div>
                    <div class="flex items-center space-x-2 mb-4">
                        <div class="w-8 h-8 bg-gradient-to-r from-orange-500 to-red-500 rounded-sm flex items-center justify-center">
                            <span class="text-white font-black text-sm">H</span>
                        </div>
                        <div>
                            <h4 class="font-black flex items-center space-x-1">
                                <span>HUSTLE</span>
                                <span class="text-sm">🔥</span>
                                <span>SUPPLY</span>
                                <span class="text-sm">💎</span>
                            </h4>
                            <p class="text-xs text-gray-400 flex items-center space-x-1">
                                <span>🏙️</span>
                                <span>Crafted for the Grind</span>
                                <span>⚡</span>
                            </p>
                        </div>
                    </div>
                    <p class="text-gray-400 text-sm flex items-center space-x-1">
                        <span>🎯</span>
                        <span>Premium streetwear for the relentless pursuit of greatness.</span>
                        <span>🚀</span>
                    </p>
                </div>
                
                <div>
                    <h5 class="font-bold mb-4">Shop</h5>
                    <ul class="space-y-2 text-gray-400 text-sm">
                        <li><a href="#" onclick="filterProducts('new')" class="hover:text-white transition-colors">New Arrivals</a></li>
                        <li><a href="#" onclick="filterProducts('hoodies')" class="hover:text-white transition-colors">Hoodies</a></li>
                        <li><a href="#" onclick="filterProducts('tees')" class="hover:text-white transition-colors">Tees</a></li>
                        <li><a href="#" onclick="filterProducts('accessories')" class="hover:text-white transition-colors">Accessories</a></li>
                    </ul>
                </div>
                
                <div>
                    <h5 class="font-bold mb-4">Support</h5>
                    <ul class="space-y-2 text-gray-400 text-sm">
                        <li><a href="#" class="hover:text-white transition-colors">Size Guide</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Shipping</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Returns</a></li>
                        <li><a href="#" onclick="showSection('contact')" class="hover:text-white transition-colors">Contact</a></li>
                    </ul>
                </div>
                
                <div>
                    <h5 class="font-bold mb-4">Connect</h5>
                    <div class="flex space-x-4">
                        <a href="#" class="text-gray-400 hover:text-white transition-colors">
                            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition-colors">
                            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                            </svg>
                        </a>
                    </div>
                </div>
            </div>
            
            <div class="border-t border-gray-700 mt-8 pt-8 text-center text-gray-400 text-sm">
                <p>&copy; 2024 HUSTLE SUPPLY. All rights reserved. Crafted for the Grind.</p>
            </div>
        </div>
    </footer>

    <script>
        // Global variables
        let cart = [];
        let currentUser = null;
        let users = [];
        let orders = [];
        let pendingPayments = [];
        let userActivities = [];
        let securityLogs = [];
        let currentAdminTab = 'overview';
        let selectedPaymentMethod = null;
        let securityStatus = 'secure';
        let originalHTML = document.documentElement.innerHTML;
        let currentPage = 1;
        let itemsPerPage = 20;
        let filteredProducts = [];
        let currentTheme = 'dark';
        let currentCurrency = 'USD';
        let backgroundImages = [];
        let slideshowInterval = null;
        let paymentReceivers = [];
        let customerMessages = [];
        let productReviews = [];
        let responseTemplates = [];
        let currentRatingProduct = null;
        let selectedRating = 0;
        let products = [
            { id: 1, name: 'Grind Mode Tee', price: 45, category: 'tees', description: 'Premium cotton blend with embroidered logo', emoji: '👕' },
            { id: 2, name: 'Never Stop Hoodie', price: 85, category: 'hoodies', description: 'Heavy-weight fleece with kangaroo pocket', emoji: '🧥' },
            { id: 3, name: 'Hustle Joggers', price: 65, category: 'bottoms', description: 'Tapered fit with reflective details', emoji: '👖' },
            { id: 4, name: 'Supply Snapback', price: 35, category: 'accessories', description: 'Structured crown with flat brim', emoji: '🧢' },
            { id: 5, name: 'Street Runner', price: 120, category: 'accessories', description: 'Limited edition colorway', emoji: '👟' },
            { id: 6, name: 'Daily Grind Backpack', price: 95, category: 'accessories', description: 'Water-resistant with laptop compartment', emoji: '🎒' },
            { id: 7, name: 'Hustle Crew Neck', price: 55, category: 'tees', description: 'Classic fit with vintage wash', emoji: '👕' },
            { id: 8, name: 'Grind Zip Hoodie', price: 95, category: 'hoodies', description: 'Full zip with side pockets', emoji: '🧥' },
            { id: 9, name: 'Supply Shorts', price: 45, category: 'bottoms', description: 'Mesh-lined athletic shorts', emoji: '🩳' },
            { id: 10, name: 'Hustle Beanie', price: 25, category: 'accessories', description: 'Ribbed knit with logo patch', emoji: '🧢' },
            { id: 11, name: 'Grind Tank', price: 35, category: 'tees', description: 'Muscle fit with dropped armholes', emoji: '👕' },
            { id: 12, name: 'Supply Socks', price: 15, category: 'accessories', description: 'Cushioned athletic socks 3-pack', emoji: '🧦' }
        ];
        
        // Currency exchange rates (base: USD) - All world currencies
        const exchangeRates = {
            'USD': 1, 'EUR': 0.85, 'GBP': 0.73, 'JPY': 150, 'AUD': 1.52, 'CAD': 1.35, 'CHF': 0.88, 'CNY': 7.24, 'SEK': 10.87, 'NZD': 1.64,
            'MXN': 17.12, 'SGD': 1.35, 'HKD': 7.83, 'NOK': 10.75, 'KRW': 1342, 'TRY': 29.15, 'RUB': 92.50, 'INR': 83.12, 'BRL': 4.95, 'ZAR': 18.85,
            'PLN': 4.02, 'TWD': 31.45, 'DKK': 6.89, 'THB': 35.67, 'ILS': 3.72, 'PHP': 56.23, 'CZK': 22.15, 'AED': 3.67, 'MYR': 4.68, 'HUF': 360.25,
            'CLP': 890.50, 'SAR': 3.75, 'BGN': 1.81, 'RON': 4.58, 'HRK': 6.98, 'ISK': 138.75, 'EGP': 30.85, 'QAR': 3.64, 'KWD': 0.31, 'BHD': 0.38,
            'OMR': 0.38, 'JOD': 0.71, 'LBP': 15000, 'TND': 3.12, 'DZD': 134.50, 'MAD': 10.15, 'KES': 147.25, 'NGN': 1650, 'GHS': 12.45, 'UGX': 3785,
            'TZS': 2510, 'ZMW': 26.75, 'BWP': 13.65, 'MUR': 45.20, 'SCR': 13.85, 'ETB': 55.40, 'RWF': 1285, 'XOF': 605.50, 'XAF': 605.50, 'GMD': 67.25,
            'SLL': 22500, 'LRD': 190.50, 'GNF': 8650, 'CDF': 2485, 'AOA': 825.50, 'MZN': 63.75, 'SZL': 18.85, 'LSL': 18.85, 'NAD': 18.85, 'MWK': 1685,
            'ZWL': 5.40, 'BIF': 2845, 'RSD': 108.25, 'MKD': 56.85, 'ALL': 94.50, 'BAM': 1.81, 'MDL': 17.85, 'GEL': 2.68, 'AMD': 385.50, 'AZN': 1.70,
            'BYN': 3.28, 'KZT': 452.50, 'KGS': 89.25, 'TJS': 10.95, 'TMT': 3.50, 'UZS': 12450, 'AFN': 70.25, 'PKR': 278.50, 'LKR': 325.75, 'BDT': 110.25,
            'BTN': 83.12, 'MVR': 15.45, 'NPR': 133.00, 'MMK': 2095, 'KHR': 4125, 'LAK': 21500, 'VND': 24350, 'IDR': 15750, 'MOP': 8.05, 'BND': 1.35,
            'FJD': 2.24, 'PGK': 3.75, 'SBD': 8.45, 'VUV': 119.50, 'WST': 2.72, 'TOP': 2.35, 'KPW': 900, 'MNT': 3485, 'IRR': 42000, 'IQD': 1310,
            'SYP': 13000, 'YER': 250.50, 'COP': 4125, 'PEN': 3.68, 'BOB': 6.92, 'PYG': 7285, 'UYU': 39.25, 'GYD': 209.50, 'SRD': 37.85, 'VES': 36.15,
            'CRC': 525.50, 'GTQ': 7.82, 'HNL': 24.65, 'NIO': 36.75, 'PAB': 1.00, 'DOP': 56.85, 'HTG': 132.50, 'JMD': 154.25, 'CUP': 24.00, 'BBD': 2.00,
            'BZD': 2.02, 'XCD': 2.70, 'TTD': 6.78, 'AWG': 1.80, 'ANG': 1.80, 'BMD': 1.00, 'KYD': 0.83, 'BSD': 1.00, 'FKP': 0.73, 'GIP': 0.73, 'SHP': 0.73
        };
        
        const currencySymbols = {
            'USD': '$', 'EUR': '€', 'GBP': '£', 'JPY': '¥', 'AUD': 'A$', 'CAD': 'C$', 'CHF': 'CHF', 'CNY': '¥', 'SEK': 'kr', 'NZD': 'NZ$',
            'MXN': '$', 'SGD': 'S$', 'HKD': 'HK$', 'NOK': 'kr', 'KRW': '₩', 'TRY': '₺', 'RUB': '₽', 'INR': '₹', 'BRL': 'R$', 'ZAR': 'R',
            'PLN': 'zł', 'TWD': 'NT$', 'DKK': 'kr', 'THB': '฿', 'ILS': '₪', 'PHP': '₱', 'CZK': 'Kč', 'AED': 'د.إ', 'MYR': 'RM', 'HUF': 'Ft',
            'CLP': '$', 'SAR': '﷼', 'BGN': 'лв', 'RON': 'lei', 'HRK': 'kn', 'ISK': 'kr', 'EGP': '£', 'QAR': '﷼', 'KWD': 'د.ك', 'BHD': '.د.ب',
            'OMR': '﷼', 'JOD': 'د.ا', 'LBP': '£', 'TND': 'د.ت', 'DZD': 'د.ج', 'MAD': 'د.م.', 'KES': 'KSh', 'NGN': '₦', 'GHS': '₵', 'UGX': 'USh',
            'TZS': 'TSh', 'ZMW': 'ZK', 'BWP': 'P', 'MUR': '₨', 'SCR': '₨', 'ETB': 'Br', 'RWF': 'FRw', 'XOF': 'CFA', 'XAF': 'FCFA', 'GMD': 'D',
            'SLL': 'Le', 'LRD': 'L$', 'GNF': 'FG', 'CDF': 'FC', 'AOA': 'Kz', 'MZN': 'MT', 'SZL': 'L', 'LSL': 'L', 'NAD': 'N$', 'MWK': 'MK',
            'ZWL': 'Z$', 'BIF': 'FBu', 'RSD': 'дин', 'MKD': 'ден', 'ALL': 'L', 'BAM': 'KM', 'MDL': 'L', 'GEL': '₾', 'AMD': '֏', 'AZN': '₼',
            'BYN': 'Br', 'KZT': '₸', 'KGS': 'с', 'TJS': 'SM', 'TMT': 'T', 'UZS': 'сўм', 'AFN': '؋', 'PKR': '₨', 'LKR': '₨', 'BDT': '৳',
            'BTN': 'Nu', 'MVR': 'Rf', 'NPR': '₨', 'MMK': 'K', 'KHR': '៛', 'LAK': '₭', 'VND': '₫', 'IDR': 'Rp', 'MOP': 'MOP$', 'BND': 'B$',
            'FJD': 'FJ$', 'PGK': 'K', 'SBD': 'SI$', 'VUV': 'VT', 'WST': 'WS$', 'TOP': 'T$', 'KPW': '₩', 'MNT': '₮', 'IRR': '﷼', 'IQD': 'ع.د',
            'SYP': '£', 'YER': '﷼', 'COP': '$', 'PEN': 'S/', 'BOB': 'Bs', 'PYG': '₲', 'UYU': '$U', 'GYD': 'G$', 'SRD': '$', 'VES': 'Bs',
            'CRC': '₡', 'GTQ': 'Q', 'HNL': 'L', 'NIO': 'C$', 'PAB': 'B/.', 'DOP': 'RD$', 'HTG': 'G', 'JMD': 'J$', 'CUP': '$', 'BBD': 'Bds$',
            'BZD': 'BZ$', 'XCD': 'EC$', 'TTD': 'TT$', 'AWG': 'ƒ', 'ANG': 'ƒ', 'BMD': '$', 'KYD': '$', 'BSD': '$', 'FKP': '£', 'GIP': '£', 'SHP': '£'
        };
        
        // Payment methods by country
        const paymentMethods = {
            'US': [
                { id: 'card', name: 'Credit/Debit Card', icon: '💳' },
                { id: 'paypal', name: 'PayPal', icon: '🅿️' },
                { id: 'apple-pay', name: 'Apple Pay', icon: '📱' },
                { id: 'bitcoin', name: 'Bitcoin', icon: '₿' }
            ],
            'UK': [
                { id: 'card', name: 'Credit/Debit Card', icon: '💳' },
                { id: 'paypal', name: 'PayPal', icon: '🅿️' },
                { id: 'bank-transfer', name: 'Bank Transfer', icon: '🏦' },
                { id: 'bitcoin', name: 'Bitcoin', icon: '₿' }
            ],
            'NG': [
                { id: 'card', name: 'Credit/Debit Card', icon: '💳' },
                { id: 'bank-transfer', name: 'Bank Transfer', icon: '🏦' },
                { id: 'mobile-money', name: 'Mobile Money', icon: '📱' },
                { id: 'bitcoin', name: 'Bitcoin', icon: '₿' }
            ],
            'IN': [
                { id: 'card', name: 'Credit/Debit Card', icon: '💳' },
                { id: 'upi', name: 'UPI', icon: '📱' },
                { id: 'paytm', name: 'Paytm', icon: '📱' },
                { id: 'bitcoin', name: 'Bitcoin', icon: '₿' }
            ],
            'default': [
                { id: 'card', name: 'Credit/Debit Card', icon: '💳' },
                { id: 'paypal', name: 'PayPal', icon: '🅿️' },
                { id: 'bitcoin', name: 'Bitcoin', icon: '₿' }
            ]
        };

        // Initialize app
        document.addEventListener('DOMContentLoaded', function() {
            loadProducts();
            loadFeaturedProducts();
            checkAuthState();
            startLiveActivitySimulation();
            initializeCharts();
            initializeCurrency();
            initializeTheme();
            initializeImageHandlers();
            initializeRatingSystem();
            initializeCustomerService();
            populateCurrencyOptions();
            loadStoredData();
            showComingSoonAlert();
        });

        // Welcome Message with Stars
        function showWelcomeMessage(user) {
            const welcomeOverlay = document.createElement('div');
            welcomeOverlay.className = 'fixed inset-0 bg-black bg-opacity-90 flex items-center justify-center z-50';
            welcomeOverlay.innerHTML = `
                <div class="text-center max-w-2xl mx-4">
                    <div class="mb-8">
                        <div class="text-8xl mb-4 animate-bounce">⭐</div>
                        <h1 class="text-6xl md:text-8xl font-black mb-4 bg-gradient-to-r from-orange-500 via-red-500 to-yellow-500 bg-clip-text text-transparent animate-pulse">
                            WELCOME!
                        </h1>
                        <div class="flex justify-center space-x-4 text-4xl mb-6">
                            <span class="animate-pulse">⭐</span>
                            <span class="animate-pulse" style="animation-delay: 0.2s">✨</span>
                            <span class="animate-pulse" style="animation-delay: 0.4s">🌟</span>
                            <span class="animate-pulse" style="animation-delay: 0.6s">💫</span>
                            <span class="animate-pulse" style="animation-delay: 0.8s">⭐</span>
                        </div>
                    </div>
                    
                    <div class="bg-gradient-to-r from-orange-500/20 to-red-500/20 backdrop-blur-sm rounded-2xl p-8 border border-orange-500/30">
                        <h2 class="text-3xl font-bold text-white mb-4">
                            🔥 Welcome to the Grind, ${user.username}! 💎
                        </h2>
                        <p class="text-xl text-gray-300 mb-6">
                            ${user.country ? getCountryFlag(user.country) : '🌍'} Ready to hustle from ${user.country ? getCountryName(user.country) : 'around the world'}?
                        </p>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6 text-sm">
                            <div class="bg-black/30 rounded-lg p-4">
                                <div class="text-2xl mb-2">🛍️</div>
                                <p class="text-orange-400 font-bold">SHOP PREMIUM</p>
                                <p class="text-gray-400">Exclusive streetwear</p>
                            </div>
                            <div class="bg-black/30 rounded-lg p-4">
                                <div class="text-2xl mb-2">📦</div>
                                <p class="text-green-400 font-bold">REQUEST PRODUCTS</p>
                                <p class="text-gray-400">Custom orders available</p>
                            </div>
                            <div class="bg-black/30 rounded-lg p-4">
                                <div class="text-2xl mb-2">⚡</div>
                                <p class="text-blue-400 font-bold">FAST SUPPORT</p>
                                <p class="text-gray-400">24/7 customer service</p>
                            </div>
                        </div>
                        <button onclick="closeWelcomeMessage()" class="bg-gradient-to-r from-orange-500 to-red-500 text-white px-8 py-4 rounded-lg font-bold text-lg hover:from-orange-600 hover:to-red-600 transition-all transform hover:scale-105">
                            🚀 START SHOPPING 🚀
                        </button>
                    </div>
                </div>
            `;
            
            document.body.appendChild(welcomeOverlay);
            
            // Auto-close after 8 seconds
            setTimeout(() => {
                closeWelcomeMessage();
            }, 8000);
        }

        function closeWelcomeMessage() {
            const welcomeOverlay = document.querySelector('.fixed.inset-0.bg-black.bg-opacity-90');
            if (welcomeOverlay) {
                welcomeOverlay.remove();
            }
        }

        function getCountryFlag(countryCode) {
            const flags = {
                'US': '🇺🇸', 'GB': '🇬🇧', 'CA': '🇨🇦', 'AU': '🇦🇺', 'DE': '🇩🇪', 'FR': '🇫🇷', 'ES': '🇪🇸', 'IT': '🇮🇹',
                'NL': '🇳🇱', 'SE': '🇸🇪', 'NO': '🇳🇴', 'DK': '🇩🇰', 'FI': '🇫🇮', 'CH': '🇨🇭', 'AT': '🇦🇹', 'BE': '🇧🇪',
                'IE': '🇮🇪', 'PT': '🇵🇹', 'GR': '🇬🇷', 'PL': '🇵🇱', 'CZ': '🇨🇿', 'HU': '🇭🇺', 'RO': '🇷🇴', 'BG': '🇧🇬',
                'HR': '🇭🇷', 'SI': '🇸🇮', 'SK': '🇸🇰', 'LT': '🇱🇹', 'LV': '🇱🇻', 'EE': '🇪🇪', 'JP': '🇯🇵', 'KR': '🇰🇷',
                'CN': '🇨🇳', 'IN': '🇮🇳', 'SG': '🇸🇬', 'HK': '🇭🇰', 'TW': '🇹🇼', 'TH': '🇹🇭', 'MY': '🇲🇾', 'ID': '🇮🇩',
                'PH': '🇵🇭', 'VN': '🇻🇳', 'BD': '🇧🇩', 'PK': '🇵🇰', 'LK': '🇱🇰', 'NP': '🇳🇵', 'MM': '🇲🇲', 'KH': '🇰🇭',
                'LA': '🇱🇦', 'BN': '🇧🇳', 'MV': '🇲🇻', 'BT': '🇧🇹', 'NG': '🇳🇬', 'ZA': '🇿🇦', 'EG': '🇪🇬', 'KE': '🇰🇪',
                'GH': '🇬🇭', 'ET': '🇪🇹', 'UG': '🇺🇬', 'TZ': '🇹🇿', 'RW': '🇷🇼', 'SN': '🇸🇳', 'CI': '🇨🇮', 'CM': '🇨🇲',
                'BF': '🇧🇫', 'ML': '🇲🇱', 'NE': '🇳🇪', 'TD': '🇹🇩', 'SD': '🇸🇩', 'LY': '🇱🇾', 'TN': '🇹🇳', 'DZ': '🇩🇿',
                'MA': '🇲🇦', 'MX': '🇲🇽', 'BR': '🇧🇷', 'AR': '🇦🇷', 'CL': '🇨🇱', 'CO': '🇨🇴', 'PE': '🇵🇪', 'VE': '🇻🇪',
                'EC': '🇪🇨', 'BO': '🇧🇴', 'PY': '🇵🇾', 'UY': '🇺🇾', 'GY': '🇬🇾', 'SR': '🇸🇷', 'GF': '🇬🇫', 'CR': '🇨🇷',
                'PA': '🇵🇦', 'NI': '🇳🇮', 'HN': '🇭🇳', 'GT': '🇬🇹', 'BZ': '🇧🇿', 'SV': '🇸🇻', 'CU': '🇨🇺', 'JM': '🇯🇲',
                'HT': '🇭🇹', 'DO': '🇩🇴', 'PR': '🇵🇷', 'TT': '🇹🇹', 'BB': '🇧🇧', 'BS': '🇧🇸', 'RU': '🇷🇺', 'UA': '🇺🇦',
                'BY': '🇧🇾', 'MD': '🇲🇩', 'GE': '🇬🇪', 'AM': '🇦🇲', 'AZ': '🇦🇿', 'KZ': '🇰🇿', 'UZ': '🇺🇿', 'TM': '🇹🇲',
                'KG': '🇰🇬', 'TJ': '🇹🇯', 'MN': '🇲🇳', 'AF': '🇦🇫', 'IR': '🇮🇷', 'IQ': '🇮🇶', 'SY': '🇸🇾', 'LB': '🇱🇧',
                'JO': '🇯🇴', 'IL': '🇮🇱', 'PS': '🇵🇸', 'SA': '🇸🇦', 'AE': '🇦🇪', 'QA': '🇶🇦', 'BH': '🇧🇭', 'KW': '🇰🇼',
                'OM': '🇴🇲', 'YE': '🇾🇪', 'TR': '🇹🇷', 'CY': '🇨🇾', 'MT': '🇲🇹', 'IS': '🇮🇸', 'GL': '🇬🇱', 'FO': '🇫🇴',
                'NZ': '🇳🇿', 'FJ': '🇫🇯', 'PG': '🇵🇬', 'SB': '🇸🇧', 'VU': '🇻🇺', 'NC': '🇳🇨', 'PF': '🇵🇫', 'WS': '🇼🇸',
                'TO': '🇹🇴', 'KI': '🇰🇮', 'TV': '🇹🇻', 'NR': '🇳🇷', 'PW': '🇵🇼', 'FM': '🇫🇲', 'MH': '🇲🇭'
            };
            return flags[countryCode] || '🌍';
        }

        function getCountryName(countryCode) {
            const countries = {
                'US': 'United States', 'GB': 'United Kingdom', 'CA': 'Canada', 'AU': 'Australia', 'DE': 'Germany',
                'FR': 'France', 'ES': 'Spain', 'IT': 'Italy', 'NL': 'Netherlands', 'SE': 'Sweden', 'NO': 'Norway',
                'DK': 'Denmark', 'FI': 'Finland', 'CH': 'Switzerland', 'AT': 'Austria', 'BE': 'Belgium', 'IE': 'Ireland',
                'PT': 'Portugal', 'GR': 'Greece', 'PL': 'Poland', 'CZ': 'Czech Republic', 'HU': 'Hungary', 'RO': 'Romania',
                'BG': 'Bulgaria', 'HR': 'Croatia', 'SI': 'Slovenia', 'SK': 'Slovakia', 'LT': 'Lithuania', 'LV': 'Latvia',
                'EE': 'Estonia', 'JP': 'Japan', 'KR': 'South Korea', 'CN': 'China', 'IN': 'India', 'SG': 'Singapore',
                'HK': 'Hong Kong', 'TW': 'Taiwan', 'TH': 'Thailand', 'MY': 'Malaysia', 'ID': 'Indonesia', 'PH': 'Philippines',
                'VN': 'Vietnam', 'BD': 'Bangladesh', 'PK': 'Pakistan', 'LK': 'Sri Lanka', 'NP': 'Nepal', 'MM': 'Myanmar',
                'KH': 'Cambodia', 'LA': 'Laos', 'BN': 'Brunei', 'MV': 'Maldives', 'BT': 'Bhutan', 'NG': 'Nigeria',
                'ZA': 'South Africa', 'EG': 'Egypt', 'KE': 'Kenya', 'GH': 'Ghana', 'ET': 'Ethiopia', 'UG': 'Uganda',
                'TZ': 'Tanzania', 'RW': 'Rwanda', 'SN': 'Senegal', 'CI': 'Ivory Coast', 'CM': 'Cameroon', 'BF': 'Burkina Faso',
                'ML': 'Mali', 'NE': 'Niger', 'TD': 'Chad', 'SD': 'Sudan', 'LY': 'Libya', 'TN': 'Tunisia', 'DZ': 'Algeria',
                'MA': 'Morocco', 'MX': 'Mexico', 'BR': 'Brazil', 'AR': 'Argentina', 'CL': 'Chile', 'CO': 'Colombia',
                'PE': 'Peru', 'VE': 'Venezuela', 'EC': 'Ecuador', 'BO': 'Bolivia', 'PY': 'Paraguay', 'UY': 'Uruguay',
                'GY': 'Guyana', 'SR': 'Suriname', 'GF': 'French Guiana', 'CR': 'Costa Rica', 'PA': 'Panama', 'NI': 'Nicaragua',
                'HN': 'Honduras', 'GT': 'Guatemala', 'BZ': 'Belize', 'SV': 'El Salvador', 'CU': 'Cuba', 'JM': 'Jamaica',
                'HT': 'Haiti', 'DO': 'Dominican Republic', 'PR': 'Puerto Rico', 'TT': 'Trinidad and Tobago', 'BB': 'Barbados',
                'BS': 'Bahamas', 'RU': 'Russia', 'UA': 'Ukraine', 'BY': 'Belarus', 'MD': 'Moldova', 'GE': 'Georgia',
                'AM': 'Armenia', 'AZ': 'Azerbaijan', 'KZ': 'Kazakhstan', 'UZ': 'Uzbekistan', 'TM': 'Turkmenistan',
                'KG': 'Kyrgyzstan', 'TJ': 'Tajikistan', 'MN': 'Mongolia', 'AF': 'Afghanistan', 'IR': 'Iran', 'IQ': 'Iraq',
                'SY': 'Syria', 'LB': 'Lebanon', 'JO': 'Jordan', 'IL': 'Israel', 'PS': 'Palestine', 'SA': 'Saudi Arabia',
                'AE': 'UAE', 'QA': 'Qatar', 'BH': 'Bahrain', 'KW': 'Kuwait', 'OM': 'Oman', 'YE': 'Yemen', 'TR': 'Turkey',
                'CY': 'Cyprus', 'MT': 'Malta', 'IS': 'Iceland', 'GL': 'Greenland', 'FO': 'Faroe Islands', 'NZ': 'New Zealand',
                'FJ': 'Fiji', 'PG': 'Papua New Guinea', 'SB': 'Solomon Islands', 'VU': 'Vanuatu', 'NC': 'New Caledonia',
                'PF': 'French Polynesia', 'WS': 'Samoa', 'TO': 'Tonga', 'KI': 'Kiribati', 'TV': 'Tuvalu', 'NR': 'Nauru',
                'PW': 'Palau', 'FM': 'Micronesia', 'MH': 'Marshall Islands'
            };
            return countries[countryCode] || 'the World';
        }

        // Product Request Functions
        function showProductRequestModal(productId) {
            if (!currentUser) {
                alert('Please login to request products');
                showModal('login');
                return;
            }
            
            const product = products.find(p => p.id === productId);
            if (!product) return;
            
            document.getElementById('request-product-name').textContent = `${product.emoji} ${product.name}`;
            showModal('product-request');
        }

        // Product Request Form Handler
        document.getElementById('product-request-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser) {
                alert('Please login to send a product request');
                return;
            }
            
            const productName = document.getElementById('request-product-name').textContent;
            const request = {
                id: customerMessages.length + 1,
                customerId: currentUser.id,
                customerName: currentUser.username,
                customerEmail: currentUser.email,
                subject: 'product-request',
                productName: productName,
                requestType: document.getElementById('request-type').value,
                quantity: document.getElementById('request-quantity').value,
                details: document.getElementById('request-details').value,
                budget: document.getElementById('request-budget').value,
                timeline: document.getElementById('request-timeline').value,
                notifyAvailability: document.getElementById('notify-availability').checked,
                message: `Product Request: ${productName}\n\nType: ${document.getElementById('request-type').value}\nQuantity: ${document.getElementById('request-quantity').value}\nDetails: ${document.getElementById('request-details').value}\nBudget: ${document.getElementById('request-budget').value || 'Not specified'}\nTimeline: ${document.getElementById('request-timeline').value}\nNotify when available: ${document.getElementById('notify-availability').checked ? 'Yes' : 'No'}`,
                priority: 'medium',
                status: 'unread',
                timestamp: new Date().toISOString(),
                responses: [],
                type: 'product-request'
            };
            
            customerMessages.unshift(request);
            localStorage.setItem('customerMessages', JSON.stringify(customerMessages));
            
            updateCustomerMessagesCount();
            hideModal('product-request');
            this.reset();
            
            // Show success message
            const successAlert = document.createElement('div');
            successAlert.className = 'fixed top-4 right-4 bg-gradient-to-r from-green-500 to-green-600 text-white p-4 rounded-lg shadow-lg z-50 max-w-sm';
            successAlert.innerHTML = `
                <div class="flex items-start space-x-3">
                    <div class="text-2xl">📦</div>
                    <div class="flex-1">
                        <h4 class="font-bold mb-1">Request Sent!</h4>
                        <p class="text-sm opacity-90">Your product request has been sent to our admin team. We'll contact you within 24-48 hours!</p>
                        <button onclick="this.parentElement.parentElement.parentElement.remove()" class="mt-2 text-xs underline opacity-75 hover:opacity-100">
                            Dismiss
                        </button>
                    </div>
                    <button onclick="this.parentElement.parentElement.remove()" class="text-white hover:text-gray-200">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                        </svg>
                    </button>
                </div>
            `;
            
            document.body.appendChild(successAlert);
            
            // Auto-remove after 8 seconds
            setTimeout(() => {
                if (successAlert.parentElement) {
                    successAlert.remove();
                }
            }, 8000);
            
            logActivity('Product Request', `Requested ${productName}`);
        });

        // Coming Soon Alert
        function showComingSoonAlert() {
            // Show coming soon alert after 2 seconds
            setTimeout(() => {
                const alert = document.createElement('div');
                alert.className = 'fixed top-4 right-4 bg-gradient-to-r from-orange-500 to-red-500 text-white p-4 rounded-lg shadow-lg z-50 max-w-sm';
                alert.innerHTML = `
                    <div class="flex items-start space-x-3">
                        <div class="text-2xl">🚀</div>
                        <div class="flex-1">
                            <h4 class="font-bold mb-1">App Coming Soon!</h4>
                            <p class="text-sm opacity-90">HUSTLE SUPPLY is launching soon with full e-commerce features, secure payments, and more!</p>
                            <button onclick="this.parentElement.parentElement.parentElement.remove()" class="mt-2 text-xs underline opacity-75 hover:opacity-100">
                                Dismiss
                            </button>
                        </div>
                        <button onclick="this.parentElement.parentElement.remove()" class="text-white hover:text-gray-200">
                            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                            </svg>
                        </button>
                    </div>
                `;
                
                document.body.appendChild(alert);
                
                // Auto-remove after 10 seconds
                setTimeout(() => {
                    if (alert.parentElement) {
                        alert.remove();
                    }
                }, 10000);
            }, 2000);
        }

        // Section navigation
        function showSection(sectionName) {
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(sectionName).classList.add('active');
            
            // Log navigation activity
            logActivity('Navigation', `Visited ${sectionName} section`);
            
            if (sectionName === 'shop') {
                // Initialize filtered products if not already done
                if (filteredProducts.length === 0) {
                    filteredProducts = [...products];
                }
                loadProducts();
            } else if (sectionName === 'admin' && currentUser && currentUser.isAdmin) {
                updateAdminStats();
            }
        }

        // Modal functions
        function showModal(modalName) {
            document.getElementById(modalName + '-modal').classList.remove('hidden');
        }

        function hideModal(modalName) {
            document.getElementById(modalName + '-modal').classList.add('hidden');
        }

        // Authentication
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('login-username').value;
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;
            const country = document.getElementById('login-country').value;
            
            // Allow login with either username OR email (not both required)
            const user = users.find(u => 
                (u.username === username || u.email === email) && u.password === password
            );
            
            if (user) {
                // Store country information
                user.country = country;
                currentUser = user;
                updateAuthUI();
                hideModal('login');
                
                // Show big welcome message with stars
                showWelcomeMessage(user);
                
                logActivity('User Login', `User ${user.username} logged in from ${country}`);
                
                // Store user data in localStorage for persistence
                localStorage.setItem('currentUser', JSON.stringify(user));
                localStorage.setItem('users', JSON.stringify(users));
            } else {
                alert('Invalid credentials. Please try again.');
                logSecurityEvent('Failed Login Attempt', `Invalid credentials for ${username || email}`);
            }
        });

        document.getElementById('signup-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('signup-username').value;
            const email = document.getElementById('signup-email').value;
            const password = document.getElementById('signup-password').value;
            const confirmPassword = document.getElementById('signup-confirm-password').value;
            
            if (password !== confirmPassword) {
                alert('Passwords do not match!');
                return;
            }
            
            if (users.find(u => u.username === username || u.email === email)) {
                alert('Username or email already exists!');
                return;
            }
            
            const newUser = {
                id: users.length + 1,
                username: username,
                email: email,
                password: password,
                isAdmin: username === 'admin', // Make first user or 'admin' username an admin
                joinedDate: new Date().toISOString(),
                status: 'active'
            };
            
            users.push(newUser);
            currentUser = newUser;
            updateAuthUI();
            hideModal('signup');
            alert('Account created successfully!');
            updateAdminStats();
            logActivity('User Registration', 'New user signed up');
        });

        // Password Reset
        document.getElementById('reset-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('reset-email').value;
            
            const user = users.find(u => u.email === email);
            if (user) {
                // In a real app, this would send an actual email
                alert('Password reset link sent to your email! (Demo: Check console for reset token)');
                console.log('Reset token for', email, ':', Math.random().toString(36).substr(2, 9));
                hideModal('reset');
            } else {
                alert('Email not found in our system.');
            }
        });

        function logout() {
            currentUser = null;
            updateAuthUI();
            showSection('home');
        }

        function updateAuthUI() {
            const userMenu = document.getElementById('user-menu');
            const authButtons = document.getElementById('auth-buttons');
            const adminBtn = document.getElementById('admin-btn');
            
            if (currentUser) {
                document.getElementById('user-name').textContent = currentUser.username;
                userMenu.classList.remove('hidden');
                authButtons.classList.add('hidden');
                
                if (currentUser.isAdmin) {
                    adminBtn.classList.remove('hidden');
                }
            } else {
                userMenu.classList.add('hidden');
                authButtons.classList.remove('hidden');
                adminBtn.classList.add('hidden');
            }
        }

        function checkAuthState() {
            // Load stored data from localStorage
            const storedUser = localStorage.getItem('currentUser');
            const storedUsers = localStorage.getItem('users');
            const storedProducts = localStorage.getItem('products');
            const storedOrders = localStorage.getItem('orders');
            
            if (storedUser) {
                currentUser = JSON.parse(storedUser);
            }
            
            if (storedUsers) {
                users = JSON.parse(storedUsers);
            }
            
            if (storedProducts) {
                products = JSON.parse(storedProducts);
            }
            
            if (storedOrders) {
                orders = JSON.parse(storedOrders);
            }
            
            updateAuthUI();
            startSecurityMonitoring();
        }

        // Product functions
        function loadProducts() {
            const container = document.getElementById('all-products');
            const startIndex = (currentPage - 1) * itemsPerPage;
            const endIndex = startIndex + itemsPerPage;
            const productsToShow = filteredProducts.slice(startIndex, endIndex);
            
            container.innerHTML = productsToShow.map(product => createProductCard(product)).join('');
            updatePagination();
        }

        function loadFeaturedProducts() {
            const container = document.getElementById('featured-products');
            const featured = products.slice(0, 3);
            container.innerHTML = featured.map(product => createProductCard(product)).join('');
        }

        function createProductCard(product) {
            const convertedPrice = convertCurrency(product.price, currentCurrency);
            const symbol = currencySymbols[currentCurrency];
            
            // Check if product has images
            const hasImages = product.images && product.images.length > 0;
            
            return `
                <div class="product-card rounded-xl p-6 hover-scale" data-category="${product.category}">
                    <div class="bg-gray-800 rounded-lg h-64 mb-4 flex items-center justify-center overflow-hidden relative cursor-pointer" onclick="viewProductImages(${product.id})">
                        ${hasImages ? `
                            <img src="${product.images[0].data || product.images[0]}" alt="${product.name}" class="w-full h-full object-cover rounded-lg transition-transform hover:scale-105">
                            ${product.images.length > 1 ? `
                                <div class="absolute top-2 right-2 bg-black bg-opacity-70 text-white text-xs px-2 py-1 rounded-full">
                                    📷 ${product.images.length}
                                </div>
                            ` : ''}
                            <div class="absolute inset-0 bg-black bg-opacity-0 hover:bg-opacity-20 transition-all rounded-lg flex items-center justify-center">
                                <div class="opacity-0 hover:opacity-100 transition-opacity">
                                    <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"></path>
                                    </svg>
                                </div>
                            </div>
                        ` : `
                            <div class="text-center">
                                <div class="w-16 h-16 bg-gradient-to-r from-orange-500 to-red-500 rounded-lg mx-auto mb-2 flex items-center justify-center">
                                    <span class="text-2xl">${product.emoji}</span>
                                </div>
                                <p class="text-gray-400 text-sm">HUSTLE ${product.category.toUpperCase()}</p>
                                <p class="text-gray-500 text-xs mt-1">Click to view details</p>
                            </div>
                        `}
                    </div>
                    <h4 class="text-xl font-bold mb-2">${product.name}</h4>
                    <p class="text-gray-400 mb-4">${product.description}</p>
                    <div class="flex justify-between items-center mb-3">
                        <span class="text-2xl font-bold">${symbol}${convertedPrice}</span>
                        <button onclick="addToCart('${product.name}', ${product.price})" class="bg-white text-black px-4 py-2 rounded-lg font-bold hover:bg-gray-200 transition-colors">
                            ADD TO CART
                        </button>
                    </div>
                    <div class="flex justify-between items-center text-sm">
                        <div class="flex items-center space-x-1">
                            ${product.averageRating ? `
                                <div class="flex text-yellow-500">
                                    ${'★'.repeat(Math.floor(product.averageRating))}${'☆'.repeat(5 - Math.floor(product.averageRating))}
                                </div>
                                <span class="text-gray-400">(${product.reviewCount || 0})</span>
                            ` : `
                                <span class="text-gray-400">No reviews yet</span>
                            `}
                        </div>
                        <div class="flex space-x-2">
                            <button onclick="showRatingModal(${product.id})" class="text-orange-500 hover:text-orange-400 text-xs">
                                ⭐ Rate
                            </button>
                            <button onclick="showProductRequestModal(${product.id})" class="text-green-500 hover:text-green-400 text-xs">
                                📦 Request
                            </button>
                            <button onclick="showModal('customer-service')" class="text-blue-500 hover:text-blue-400 text-xs">
                                💬 Support
                            </button>
                        </div>
                    </div>
                </div>
            `;
        }

        function filterProducts(category) {
            const filterBtns = document.querySelectorAll('.filter-btn');
            
            // Update active filter button
            filterBtns.forEach(btn => {
                btn.classList.remove('active', 'bg-orange-500', 'text-white');
                btn.classList.add('bg-gray-700', 'hover:bg-gray-600');
            });
            
            if (event && event.target) {
                event.target.classList.add('active', 'bg-orange-500', 'text-white');
                event.target.classList.remove('bg-gray-700', 'hover:bg-gray-600');
            }
            
            // Filter products
            if (category === 'all') {
                filteredProducts = [...products];
            } else {
                filteredProducts = products.filter(product => product.category === category);
            }
            
            currentPage = 1; // Reset to first page
            loadProducts();
            
            // If filtering from collections, show shop section
            showSection('shop');
        }

        // Admin Tab Navigation
        function showAdminTab(tabName) {
            // Update tab buttons
            document.querySelectorAll('.admin-tab-btn').forEach(btn => {
                btn.classList.remove('active', 'bg-orange-500', 'text-white');
                btn.classList.add('bg-gray-700', 'hover:bg-gray-600');
            });
            event.target.classList.add('active', 'bg-orange-500', 'text-white');
            event.target.classList.remove('bg-gray-700', 'hover:bg-gray-600');
            
            // Show selected tab
            document.querySelectorAll('.admin-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            document.getElementById('admin-' + tabName).classList.add('active');
            
            currentAdminTab = tabName;
            
            // Load tab-specific content
            if (tabName === 'live-activity') {
                updateLiveActivity();
            } else if (tabName === 'users') {
                updateUsersTable();
            } else if (tabName === 'payments') {
                updatePaymentsTab();
            } else if (tabName === 'products') {
                updateProductManagement();
            } else if (tabName === 'customer-service') {
                updateCustomerMessages();
                updateProductReviews();
                updateResponseTemplatesList();
                updatePaymentReceiversList();
            } else if (tabName === 'attack-monitor') {
                updateAttackMonitor();
            }
        }

        // Admin functions
        document.getElementById('add-product-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser || !currentUser.isAdmin) {
                alert('Access denied!');
                return;
            }
            
            const name = document.getElementById('product-name').value;
            const price = parseInt(document.getElementById('product-price').value);
            const category = document.getElementById('product-category').value;
            const description = document.getElementById('product-description').value;
            
            const emojis = {
                'tees': '👕',
                'hoodies': '🧥',
                'bottoms': '👖',
                'accessories': '🧢'
            };
            
            const newProduct = {
                id: products.length + 1,
                name: name,
                price: price,
                category: category,
                description: description,
                emoji: emojis[category] || '👕'
            };
            
            products.push(newProduct);
            loadProducts();
            loadFeaturedProducts();
            updateAdminStats();
            updateProductManagement();
            
            // Reset form
            this.reset();
            alert('Product added successfully!');
            logActivity('Product Management', `Added new product: ${name}`);
        });

        function updateAdminStats() {
            const totalRevenue = orders.reduce((sum, order) => sum + order.total, 0);
            document.getElementById('total-products').textContent = products.length;
            document.getElementById('total-users').textContent = users.length;
            document.getElementById('total-orders').textContent = orders.length;
            document.getElementById('total-revenue').textContent = `$${totalRevenue}`;
        }

        function updateUsersTable() {
            const usersTable = document.getElementById('users-table');
            if (users.length === 0) {
                usersTable.innerHTML = '<tr><td colspan="6" class="text-center text-gray-400 py-8">No users registered yet</td></tr>';
            } else {
                usersTable.innerHTML = users.map(user => `
                    <tr class="border-b border-gray-700">
                        <td class="py-3">${user.username}</td>
                        <td class="py-3">${user.email}</td>
                        <td class="py-3">
                            <span class="px-2 py-1 rounded text-xs ${user.isAdmin ? 'bg-orange-500' : 'bg-gray-600'}">${user.isAdmin ? 'Admin' : 'User'}</span>
                        </td>
                        <td class="py-3">${new Date(user.joinedDate).toLocaleDateString()}</td>
                        <td class="py-3">
                            <span class="px-2 py-1 rounded text-xs ${user.status === 'active' ? 'bg-green-600' : 'bg-red-600'}">${user.status}</span>
                        </td>
                        <td class="py-3">
                            <button onclick="toggleUserStatus(${user.id})" class="text-orange-500 hover:text-orange-400 text-sm">Toggle Status</button>
                        </td>
                    </tr>
                `).join('');
            }
        }

        function updateProductManagement() {
            const productManagement = document.getElementById('product-management');
            productManagement.innerHTML = products.map(product => {
                const hasImages = product.images && product.images.length > 0;
                return `
                    <div class="bg-gray-800 p-4 rounded-lg">
                        <div class="flex justify-between items-start mb-3">
                            <div class="flex-1">
                                <p class="font-medium">${product.name}</p>
                                <p class="text-sm text-gray-400">$${product.price} - ${product.category}</p>
                                <p class="text-xs text-gray-500">${hasImages ? `${product.images.length} images` : 'No images'}</p>
                            </div>
                            <div class="flex space-x-2">
                                <button onclick="addImageToProduct(${product.id})" class="bg-blue-600 hover:bg-blue-700 px-3 py-1 rounded text-xs" title="Add Images">
                                    📷 Add
                                </button>
                                ${hasImages ? `
                                    <button onclick="viewProductImages(${product.id})" class="bg-green-600 hover:bg-green-700 px-3 py-1 rounded text-xs" title="View Images">
                                        👁️ View
                                    </button>
                                ` : ''}
                                <button onclick="removeProduct(${product.id})" class="bg-red-600 hover:bg-red-700 px-3 py-1 rounded text-xs">
                                    🗑️ Remove
                                </button>
                            </div>
                        </div>
                        ${hasImages ? `
                            <div class="flex space-x-2 mt-2">
                                ${product.images.slice(0, 3).map(img => `
                                    <div class="relative">
                                        <img src="${img.data || img}" alt="Product image" class="w-12 h-12 object-cover rounded border border-gray-600">
                                        <button onclick="removeImageFromProduct(${product.id}, '${img.id}')" class="absolute -top-1 -right-1 w-4 h-4 bg-red-500 rounded-full text-white text-xs flex items-center justify-center hover:bg-red-600" title="Remove Image">×</button>
                                    </div>
                                `).join('')}
                                ${product.images.length > 3 ? `
                                    <div class="w-12 h-12 bg-gray-700 rounded border border-gray-600 flex items-center justify-center text-xs text-gray-400">
                                        +${product.images.length - 3}
                                    </div>
                                ` : ''}
                            </div>
                        ` : ''}
                    </div>
                `;
            }).join('');
        }

        function removeProduct(productId) {
            if (confirm('Are you sure you want to remove this product?')) {
                products = products.filter(p => p.id !== productId);
                loadProducts();
                loadFeaturedProducts();
                updateAdminStats();
                updateProductManagement();
                logActivity('Product Management', 'Removed product');
            }
        }

        function toggleUserStatus(userId) {
            const user = users.find(u => u.id === userId);
            if (user) {
                user.status = user.status === 'active' ? 'suspended' : 'active';
                updateUsersTable();
                logActivity('User Management', `Changed user status: ${user.username}`);
            }
        }

        // Checkout Functions
        function showCheckout() {
            if (cart.length === 0) {
                alert('Your cart is empty!');
                return;
            }
            
            if (!currentUser) {
                alert('Please login to checkout');
                showModal('login');
                return;
            }
            
            updateCheckoutSummary();
            showModal('checkout');
        }

        function updateCheckoutSummary() {
            const checkoutItems = document.getElementById('checkout-items');
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const shipping = 10;
            const tax = Math.round(subtotal * 0.08); // 8% tax
            const total = subtotal + shipping + tax;
            
            checkoutItems.innerHTML = cart.map(item => `
                <div class="flex justify-between items-center">
                    <span>${item.name} x${item.quantity}</span>
                    <span>$${item.price * item.quantity}</span>
                </div>
            `).join('');
            
            document.getElementById('checkout-subtotal').textContent = `$${subtotal}`;
            document.getElementById('checkout-shipping').textContent = `$${shipping}`;
            document.getElementById('checkout-tax').textContent = `$${tax}`;
            document.getElementById('checkout-total').textContent = `$${total}`;
        }

        // Update payment methods based on country
        document.getElementById('country').addEventListener('change', function() {
            const country = this.value;
            const methods = paymentMethods[country] || paymentMethods.default;
            const paymentMethodsDiv = document.getElementById('payment-methods');
            
            paymentMethodsDiv.innerHTML = methods.map(method => `
                <label class="flex items-center space-x-3 p-3 bg-gray-800 rounded-lg cursor-pointer hover:bg-gray-700">
                    <input type="radio" name="payment-method" value="${method.id}" onchange="selectPaymentMethod('${method.id}')">
                    <span class="text-2xl">${method.icon}</span>
                    <span>${method.name}</span>
                </label>
            `).join('');
        });

        function selectPaymentMethod(methodId) {
            selectedPaymentMethod = methodId;
            
            // Hide all payment forms
            document.getElementById('card-form').classList.add('hidden');
            document.getElementById('bitcoin-form').classList.add('hidden');
            document.getElementById('mobile-form').classList.add('hidden');
            
            // Show selected payment form
            if (methodId === 'card' || methodId === 'paypal') {
                document.getElementById('card-form').classList.remove('hidden');
            } else if (methodId === 'bitcoin') {
                document.getElementById('bitcoin-form').classList.remove('hidden');
            } else if (methodId.includes('mobile') || methodId === 'upi' || methodId === 'paytm') {
                document.getElementById('mobile-form').classList.remove('hidden');
            }
            
            document.getElementById('payment-form').classList.remove('hidden');
        }

        function processPayment() {
            if (!selectedPaymentMethod) {
                alert('Please select a payment method');
                return;
            }
            
            // Validate shipping form
            const requiredFields = ['first-name', 'last-name', 'checkout-email', 'phone', 'address', 'city', 'zip-code', 'country'];
            for (let field of requiredFields) {
                if (!document.getElementById(field).value) {
                    alert('Please fill in all shipping information');
                    return;
                }
            }
            
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const total = subtotal + 10 + Math.round(subtotal * 0.08); // shipping + tax
            
            const order = {
                id: orders.length + 1,
                customerId: currentUser.id,
                customerName: currentUser.username,
                items: [...cart],
                total: total,
                paymentMethod: selectedPaymentMethod,
                status: 'pending',
                date: new Date().toISOString(),
                shippingAddress: {
                    name: `${document.getElementById('first-name').value} ${document.getElementById('last-name').value}`,
                    address: document.getElementById('address').value,
                    city: document.getElementById('city').value,
                    zipCode: document.getElementById('zip-code').value,
                    country: document.getElementById('country').value
                }
            };
            
            orders.push(order);
            pendingPayments.push(order);
            
            // Clear cart
            cart = [];
            updateCartDisplay();
            updateCartCount();
            
            hideModal('checkout');
            alert('Order placed successfully! Payment pending admin authorization.');
            
            logActivity('Order Placed', `Order #${order.id} - $${total}`);
            updateAdminStats();
        }

        // Cart functions
        // Live Activity Monitoring
        function logActivity(action, details) {
            const activity = {
                id: userActivities.length + 1,
                user: currentUser ? currentUser.username : 'Guest',
                action: action,
                details: details,
                timestamp: new Date(),
                page: getCurrentPage(),
                location: getRandomLocation()
            };
            
            userActivities.unshift(activity); // Add to beginning
            if (userActivities.length > 100) {
                userActivities = userActivities.slice(0, 100); // Keep only last 100
            }
            
            updateLiveActivity();
        }

        function getCurrentPage() {
            const activeSection = document.querySelector('.section.active');
            return activeSection ? activeSection.id : 'home';
        }

        function getRandomLocation() {
            const locations = ['New York, US', 'London, UK', 'Tokyo, JP', 'Lagos, NG', 'Sydney, AU', 'Berlin, DE', 'Mumbai, IN', 'Toronto, CA'];
            return locations[Math.floor(Math.random() * locations.length)];
        }

        function updateLiveActivity() {
            const activityFeed = document.getElementById('activity-feed');
            const activityTable = document.getElementById('activity-table');
            
            if (userActivities.length === 0) {
                activityFeed.innerHTML = '<p class="text-gray-400 text-center py-8">No recent activity</p>';
                activityTable.innerHTML = '<tr><td colspan="6" class="text-center text-gray-400 py-8">No activity data</td></tr>';
                return;
            }
            
            // Update activity feed
            activityFeed.innerHTML = userActivities.slice(0, 10).map(activity => `
                <div class="flex items-start space-x-3 p-3 bg-gray-800 rounded-lg">
                    <div class="w-2 h-2 bg-green-500 rounded-full mt-2 flex-shrink-0"></div>
                    <div class="flex-1">
                        <p class="text-sm font-medium">${activity.user}</p>
                        <p class="text-xs text-gray-400">${activity.action}: ${activity.details}</p>
                        <p class="text-xs text-gray-500">${activity.timestamp.toLocaleTimeString()}</p>
                    </div>
                </div>
            `).join('');
            
            // Update activity table
            activityTable.innerHTML = userActivities.slice(0, 20).map(activity => `
                <tr class="border-b border-gray-700">
                    <td class="py-3">${activity.user}</td>
                    <td class="py-3">${activity.action}</td>
                    <td class="py-3">${activity.page}</td>
                    <td class="py-3">${activity.timestamp.toLocaleTimeString()}</td>
                    <td class="py-3">${activity.location}</td>
                    <td class="py-3">
                        <span class="px-2 py-1 rounded text-xs bg-green-600">Active</span>
                    </td>
                </tr>
            `).join('');
        }

        function updatePaymentsTab() {
            const paymentQueue = document.getElementById('payment-queue');
            const paymentHistory = document.getElementById('payment-history');
            const pendingCount = document.getElementById('pending-payments');
            
            pendingCount.textContent = `${pendingPayments.length} Pending`;
            
            if (pendingPayments.length === 0) {
                paymentQueue.innerHTML = '<p class="text-gray-400 text-center py-8">No pending payments</p>';
            } else {
                paymentQueue.innerHTML = pendingPayments.map(payment => `
                    <div class="bg-gray-800 p-4 rounded-lg">
                        <div class="flex justify-between items-start mb-3">
                            <div>
                                <h5 class="font-bold">Order #${payment.id}</h5>
                                <p class="text-sm text-gray-400">${payment.customerName} - $${payment.total}</p>
                                <p class="text-xs text-gray-500">${payment.paymentMethod.toUpperCase()}</p>
                            </div>
                            <div class="flex space-x-2">
                                <button onclick="approvePayment(${payment.id})" class="bg-green-600 hover:bg-green-700 px-3 py-1 rounded text-sm">Approve</button>
                                <button onclick="rejectPayment(${payment.id})" class="bg-red-600 hover:bg-red-700 px-3 py-1 rounded text-sm">Reject</button>
                            </div>
                        </div>
                        <div class="text-xs text-gray-400">
                            <p>Items: ${payment.items.map(item => `${item.name} x${item.quantity}`).join(', ')}</p>
                            <p>Address: ${payment.shippingAddress.address}, ${payment.shippingAddress.city}</p>
                        </div>
                    </div>
                `).join('');
            }
            
            // Payment history
            const completedOrders = orders.filter(order => order.status !== 'pending');
            if (completedOrders.length === 0) {
                paymentHistory.innerHTML = '<tr><td colspan="6" class="text-center text-gray-400 py-8">No payment history</td></tr>';
            } else {
                paymentHistory.innerHTML = completedOrders.map(order => `
                    <tr class="border-b border-gray-700">
                        <td class="py-3">#${order.id}</td>
                        <td class="py-3">${order.customerName}</td>
                        <td class="py-3">$${order.total}</td>
                        <td class="py-3">${order.paymentMethod.toUpperCase()}</td>
                        <td class="py-3">
                            <span class="px-2 py-1 rounded text-xs ${order.status === 'approved' ? 'bg-green-600' : 'bg-red-600'}">${order.status}</span>
                        </td>
                        <td class="py-3">${new Date(order.date).toLocaleDateString()}</td>
                    </tr>
                `).join('');
            }
        }

        function approvePayment(orderId) {
            const order = pendingPayments.find(p => p.id === orderId);
            if (order) {
                order.status = 'approved';
                pendingPayments = pendingPayments.filter(p => p.id !== orderId);
                updatePaymentsTab();
                updateAdminStats();
                logActivity('Payment Authorization', `Approved payment for Order #${orderId}`);
                alert('Payment approved successfully!');
            }
        }

        function rejectPayment(orderId) {
            const order = pendingPayments.find(p => p.id === orderId);
            if (order) {
                order.status = 'rejected';
                pendingPayments = pendingPayments.filter(p => p.id !== orderId);
                updatePaymentsTab();
                logActivity('Payment Authorization', `Rejected payment for Order #${orderId}`);
                alert('Payment rejected.');
            }
        }

        function startLiveActivitySimulation() {
            // Simulate some initial activity
            setTimeout(() => logActivity('Page View', 'Visited homepage'), 1000);
            setTimeout(() => logActivity('Product View', 'Viewed Grind Mode Tee'), 3000);
            setTimeout(() => logActivity('Navigation', 'Browsed shop section'), 5000);
            
            // Continue simulating activity every 10-30 seconds
            setInterval(() => {
                const actions = ['Page View', 'Product View', 'Search', 'Filter Applied', 'Navigation'];
                const details = ['Homepage visit', 'Product browsing', 'Search query', 'Category filter', 'Section navigation'];
                const randomAction = actions[Math.floor(Math.random() * actions.length)];
                const randomDetail = details[Math.floor(Math.random() * details.length)];
                
                // Simulate guest activity
                const guestActivity = {
                    id: userActivities.length + 1,
                    user: 'Guest User',
                    action: randomAction,
                    details: randomDetail,
                    timestamp: new Date(),
                    page: getCurrentPage(),
                    location: getRandomLocation()
                };
                
                userActivities.unshift(guestActivity);
                if (userActivities.length > 100) {
                    userActivities = userActivities.slice(0, 100);
                }
                
                if (currentAdminTab === 'live-activity') {
                    updateLiveActivity();
                }
            }, Math.random() * 20000 + 10000); // Random interval between 10-30 seconds
        }

        function initializeCharts() {
            // This would initialize Chart.js charts in a real implementation
            // For demo purposes, we'll just add placeholder text
            const salesChart = document.getElementById('salesChart');
            const activeUsersChart = document.getElementById('activeUsersChart');
            const pageViewsChart = document.getElementById('pageViewsChart');
            
            if (salesChart) {
                const ctx = salesChart.getContext('2d');
                ctx.fillStyle = '#f97316';
                ctx.fillRect(0, 0, 400, 200);
                ctx.fillStyle = '#ffffff';
                ctx.font = '16px Inter';
                ctx.textAlign = 'center';
                ctx.fillText('Sales Chart (Demo)', 200, 100);
            }
            
            if (activeUsersChart) {
                const ctx = activeUsersChart.getContext('2d');
                ctx.fillStyle = '#10b981';
                ctx.fillRect(0, 0, 300, 150);
                ctx.fillStyle = '#ffffff';
                ctx.font = '14px Inter';
                ctx.textAlign = 'center';
                ctx.fillText('Active Users Chart', 150, 75);
            }
            
            if (pageViewsChart) {
                const ctx = pageViewsChart.getContext('2d');
                ctx.fillStyle = '#3b82f6';
                ctx.fillRect(0, 0, 300, 150);
                ctx.fillStyle = '#ffffff';
                ctx.font = '14px Inter';
                ctx.textAlign = 'center';
                ctx.fillText('Page Views Chart', 150, 75);
            }
        }

        function addToCart(productName, price) {
            const existingItem = cart.find(item => item.name === productName);
            
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({
                    name: productName,
                    price: price,
                    quantity: 1
                });
            }
            
            updateCartDisplay();
            updateCartCount();
            logActivity('Add to Cart', `Added ${productName} to cart`);
            
            // Show success feedback
            const button = event.target;
            const originalText = button.textContent;
            button.textContent = 'ADDED!';
            button.style.backgroundColor = '#10b981';
            
            setTimeout(() => {
                button.textContent = originalText;
                button.style.backgroundColor = '';
            }, 1000);
        }

        function removeFromCart(productName) {
            cart = cart.filter(item => item.name !== productName);
            updateCartDisplay();
            updateCartCount();
        }

        function updateQuantity(productName, change) {
            const item = cart.find(item => item.name === productName);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productName);
                } else {
                    updateCartDisplay();
                    updateCartCount();
                }
            }
        }

        function updateCartDisplay() {
            const cartItems = document.getElementById('cart-items');
            const cartTotal = document.getElementById('cart-total');
            const totalAmount = document.getElementById('total-amount');
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<p class="text-gray-400 text-center py-8">Your cart is empty</p>';
                cartTotal.classList.add('hidden');
            } else {
                let total = 0;
                cartItems.innerHTML = cart.map(item => {
                    const itemTotal = item.price * item.quantity;
                    total += itemTotal;
                    return `
                        <div class="flex justify-between items-center bg-gray-800 p-4 rounded-lg">
                            <div class="flex-1">
                                <h4 class="font-medium">${item.name}</h4>
                                <p class="text-gray-400 text-sm">$${item.price} each</p>
                            </div>
                            <div class="flex items-center space-x-2">
                                <button onclick="updateQuantity('${item.name}', -1)" class="w-6 h-6 bg-gray-700 rounded text-sm hover:bg-gray-600">-</button>
                                <span class="w-8 text-center">${item.quantity}</span>
                                <button onclick="updateQuantity('${item.name}', 1)" class="w-6 h-6 bg-gray-700 rounded text-sm hover:bg-gray-600">+</button>
                                <button onclick="removeFromCart('${item.name}')" class="ml-2 text-red-400 hover:text-red-300">×</button>
                            </div>
                        </div>
                    `;
                }).join('');
                
                totalAmount.textContent = `$${total}`;
                cartTotal.classList.remove('hidden');
            }
        }

        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            const cartCountElement = document.getElementById('cart-count');
            cartCountElement.textContent = count;
            
            if (count > 0) {
                cartCountElement.classList.add('cart-count');
                setTimeout(() => cartCountElement.classList.remove('cart-count'), 500);
            }
        }

        function toggleCart() {
            const sidebar = document.getElementById('cart-sidebar');
            sidebar.classList.toggle('translate-x-full');
        }

        // Close modals and cart when clicking outside
        document.addEventListener('click', function(event) {
            // Close cart
            const sidebar = document.getElementById('cart-sidebar');
            const cartButton = event.target.closest('button[onclick="toggleCart()"]');
            
            if (!sidebar.contains(event.target) && !cartButton && !sidebar.classList.contains('translate-x-full')) {
                sidebar.classList.add('translate-x-full');
            }
            
            // Close modals
            const modals = document.querySelectorAll('.modal');
            modals.forEach(modal => {
                if (event.target === modal) {
                    modal.classList.add('hidden');
                }
            });
        });

        // Security Functions
        function startSecurityMonitoring() {
            // Monitor for code tampering
            setInterval(() => {
                const currentHTML = document.documentElement.innerHTML;
                if (currentHTML !== originalHTML && securityStatus === 'secure') {
                    // Code has been modified
                    triggerSecurityAlert('Code Tampering Detected', 'Unauthorized modification to application code');
                }
            }, 5000);
            
            // Monitor for suspicious activities
            setInterval(() => {
                checkForSuspiciousActivity();
            }, 10000);
            
            // Monitor for developer tools
            setInterval(() => {
                detectDeveloperTools();
            }, 1000);
            
            // Monitor for right-click attempts
            document.addEventListener('contextmenu', function(e) {
                logSecurityEvent('Right-Click Attempt', `User attempted to access context menu on ${e.target.tagName}`);
                alertAdminOfAttack('Context Menu Access', 'User tried to right-click to inspect code');
            });
            
            // Monitor for F12 key attempts
            document.addEventListener('keydown', function(e) {
                if (e.key === 'F12' || (e.ctrlKey && e.shiftKey && e.key === 'I') || (e.ctrlKey && e.shiftKey && e.key === 'C') || (e.ctrlKey && e.key === 'U')) {
                    e.preventDefault();
                    logSecurityEvent('Developer Tools Attempt', `User attempted to open developer tools with ${e.key}`);
                    alertAdminOfAttack('Developer Tools Access', `User tried to access developer tools using ${e.key}`);
                    showAttackWarning();
                }
            });
            
            // Initialize security logs
            logSecurityEvent('System Start', 'Security monitoring initialized');
        }

        function triggerSecurityAlert(type, message) {
            securityStatus = 'threat';
            updateSecurityUI();
            logSecurityEvent(type, message);
            
            if (currentUser && currentUser.isAdmin) {
                alert(`🚨 SECURITY ALERT: ${type}\n${message}`);
            }
        }

        function updateSecurityUI() {
            const indicator = document.getElementById('security-indicator');
            const status = document.getElementById('security-status');
            const codeIntegrity = document.getElementById('code-integrity');
            
            if (securityStatus === 'secure') {
                indicator.className = 'w-4 h-4 bg-green-500 rounded-full animate-pulse';
                status.textContent = 'SECURE';
                status.className = 'text-sm text-green-500 font-medium';
                codeIntegrity.textContent = '✓ SAFE';
                codeIntegrity.className = 'text-green-500';
            } else {
                indicator.className = 'w-4 h-4 bg-red-500 rounded-full animate-pulse';
                status.textContent = 'THREAT DETECTED';
                status.className = 'text-sm text-red-500 font-medium';
                codeIntegrity.textContent = '⚠ COMPROMISED';
                codeIntegrity.className = 'text-red-500';
            }
            
            updateSecurityLogs();
        }

        function logSecurityEvent(type, details) {
            const event = {
                id: securityLogs.length + 1,
                type: type,
                details: details,
                timestamp: new Date(),
                severity: type.includes('Alert') || type.includes('Threat') ? 'high' : 'low'
            };
            
            securityLogs.unshift(event);
            if (securityLogs.length > 50) {
                securityLogs = securityLogs.slice(0, 50);
            }
            
            updateSecurityLogs();
        }

        function updateSecurityLogs() {
            const logsContainer = document.getElementById('security-logs');
            if (!logsContainer) return;
            
            if (securityLogs.length === 0) {
                logsContainer.innerHTML = '<p class="text-gray-400 text-center py-8">No security events</p>';
                return;
            }
            
            logsContainer.innerHTML = securityLogs.map(log => `
                <div class="flex items-start space-x-3 p-3 bg-gray-800 rounded-lg">
                    <div class="w-2 h-2 ${log.severity === 'high' ? 'bg-red-500' : 'bg-green-500'} rounded-full mt-2 flex-shrink-0"></div>
                    <div class="flex-1">
                        <p class="text-sm font-medium ${log.severity === 'high' ? 'text-red-400' : 'text-green-400'}">${log.type}</p>
                        <p class="text-xs text-gray-400">${log.details}</p>
                        <p class="text-xs text-gray-500">${log.timestamp.toLocaleString()}</p>
                    </div>
                </div>
            `).join('');
        }

        function checkForSuspiciousActivity() {
            // Check for rapid login attempts
            const recentFailedLogins = securityLogs.filter(log => 
                log.type === 'Failed Login Attempt' && 
                (new Date() - log.timestamp) < 300000 // 5 minutes
            );
            
            if (recentFailedLogins.length > 3) {
                triggerSecurityAlert('Brute Force Attack', 'Multiple failed login attempts detected');
            }
        }

        function detectDeveloperTools() {
            const threshold = 160;
            
            if (window.outerHeight - window.innerHeight > threshold || 
                window.outerWidth - window.innerWidth > threshold) {
                logSecurityEvent('Developer Tools Detected', 'Developer tools appear to be open');
                alertAdminOfAttack('Developer Tools Open', 'User has developer tools open - potential code inspection');
                showAttackWarning();
            }
        }

        function alertAdminOfAttack(attackType, details) {
            const attack = {
                id: Date.now(),
                type: attackType,
                details: details,
                timestamp: new Date(),
                userAgent: navigator.userAgent,
                ip: 'Unknown', // In real app, would get actual IP
                location: getRandomLocation(),
                severity: 'HIGH'
            };
            
            // Store attack attempt
            let attackAttempts = JSON.parse(localStorage.getItem('attackAttempts') || '[]');
            attackAttempts.unshift(attack);
            if (attackAttempts.length > 100) {
                attackAttempts = attackAttempts.slice(0, 100);
            }
            localStorage.setItem('attackAttempts', JSON.stringify(attackAttempts));
            
            // Admin can view attack attempts in the admin panel - no popup alerts
            
            // Log to security system
            logSecurityEvent(attackType, details);
        }

        function showAttackWarning() {
            // Just log silently for all users - no popup warnings
            // Admin can view attack attempts in the admin panel
        }

        function closeAttackWarning() {
            const warning = document.getElementById('attack-warning');
            if (warning) {
                warning.remove();
            }
        }

        // Customization Functions
        document.getElementById('bg-style').addEventListener('change', function() {
            const style = this.value;
            const colorOptions = document.getElementById('color-options');
            const patternOptions = document.getElementById('pattern-options');
            const imageOptions = document.getElementById('image-options');
            
            // Hide all options first
            colorOptions.classList.add('hidden');
            patternOptions.classList.add('hidden');
            imageOptions.classList.add('hidden');
            
            // Show relevant options
            if (style === 'gradient' || style === 'solid') {
                colorOptions.classList.remove('hidden');
            } else if (style === 'pattern') {
                colorOptions.classList.remove('hidden');
                patternOptions.classList.remove('hidden');
            } else if (style === 'image') {
                imageOptions.classList.remove('hidden');
            }
        });

        function applyBackgroundChanges() {
            const style = document.getElementById('bg-style').value;
            const primaryColor = document.getElementById('primary-color').value;
            const secondaryColor = document.getElementById('secondary-color').value;
            const patternType = document.getElementById('pattern-type').value;
            const image1 = document.getElementById('bg-image-1').value;
            const image2 = document.getElementById('bg-image-2').value;
            const image3 = document.getElementById('bg-image-3').value;
            const enableSlideshow = document.getElementById('enable-slideshow').checked;
            
            const body = document.body;
            
            // Clear existing slideshow
            if (slideshowInterval) {
                clearInterval(slideshowInterval);
                slideshowInterval = null;
            }
            
            // Remove existing background classes
            body.className = body.className.replace(/gradient-bg|solid-bg|pattern-bg|image-bg|slideshow-bg/g, '');
            
            switch (style) {
                case 'gradient':
                    body.style.background = `linear-gradient(135deg, ${primaryColor} 0%, ${secondaryColor} 100%)`;
                    break;
                case 'solid':
                    body.style.background = primaryColor;
                    break;
                case 'pattern':
                    body.style.background = `linear-gradient(135deg, ${primaryColor} 0%, ${secondaryColor} 100%)`;
                    // Add pattern overlay (simplified)
                    break;
                case 'image':
                    backgroundImages = [image1, image2, image3].filter(img => img.trim() !== '');
                    if (backgroundImages.length > 0) {
                        if (enableSlideshow && backgroundImages.length > 1) {
                            body.classList.add('slideshow-bg');
                            startBackgroundSlideshow();
                        } else {
                            body.style.background = `url('${backgroundImages[0]}') center/cover, linear-gradient(135deg, ${primaryColor} 0%, ${secondaryColor} 100%)`;
                        }
                    }
                    break;
            }
            
            document.getElementById('current-theme').textContent = `Custom ${style.charAt(0).toUpperCase() + style.slice(1)} Theme`;
            document.getElementById('theme-modified').textContent = new Date().toLocaleString();
            
            alert('Background updated successfully!');
            logActivity('Theme Customization', `Applied ${style} background theme`);
        }
        
        function startBackgroundSlideshow() {
            let currentImageIndex = 0;
            const body = document.body;
            
            // Set initial image
            body.style.backgroundImage = `url('${backgroundImages[currentImageIndex]}')`;
            
            // Start slideshow
            slideshowInterval = setInterval(() => {
                currentImageIndex = (currentImageIndex + 1) % backgroundImages.length;
                body.style.backgroundImage = `url('${backgroundImages[currentImageIndex]}')`;
            }, 10000); // Change every 10 seconds
        }
        
        // Pagination functions
        function updatePagination() {
            const totalPages = Math.ceil(filteredProducts.length / itemsPerPage);
            const pageInfo = document.getElementById('page-info');
            const prevBtn = document.getElementById('prev-page');
            const nextBtn = document.getElementById('next-page');
            
            pageInfo.textContent = `Page ${currentPage} of ${totalPages}`;
            
            prevBtn.disabled = currentPage === 1;
            nextBtn.disabled = currentPage === totalPages || totalPages === 0;
            
            if (prevBtn.disabled) {
                prevBtn.classList.add('opacity-50', 'cursor-not-allowed');
            } else {
                prevBtn.classList.remove('opacity-50', 'cursor-not-allowed');
            }
            
            if (nextBtn.disabled) {
                nextBtn.classList.add('opacity-50', 'cursor-not-allowed');
            } else {
                nextBtn.classList.remove('opacity-50', 'cursor-not-allowed');
            }
        }
        
        function changePage(direction) {
            const totalPages = Math.ceil(filteredProducts.length / itemsPerPage);
            const newPage = currentPage + direction;
            
            if (newPage >= 1 && newPage <= totalPages) {
                currentPage = newPage;
                loadProducts();
                
                // Scroll to top of products
                document.getElementById('all-products').scrollIntoView({ behavior: 'smooth' });
            }
        }
        
        // Theme functions
        function toggleTheme() {
            const body = document.body;
            const themeIcon = document.getElementById('theme-icon');
            
            if (currentTheme === 'dark') {
                body.classList.add('light-mode');
                currentTheme = 'light';
                // Update icon to sun
                themeIcon.innerHTML = '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path>';
            } else {
                body.classList.remove('light-mode');
                currentTheme = 'dark';
                // Update icon to moon
                themeIcon.innerHTML = '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path>';
            }
            
            localStorage.setItem('theme', currentTheme);
            logActivity('Theme Toggle', `Switched to ${currentTheme} mode`);
        }
        
        function initializeTheme() {
            const savedTheme = localStorage.getItem('theme');
            if (savedTheme) {
                currentTheme = savedTheme;
                if (currentTheme === 'light') {
                    document.body.classList.add('light-mode');
                    document.getElementById('theme-icon').innerHTML = '<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path>';
                }
            }
        }
        
        // Currency functions
        function convertCurrency(usdPrice, targetCurrency) {
            const rate = exchangeRates[targetCurrency] || 1;
            const converted = usdPrice * rate;
            
            // Format based on currency
            if (targetCurrency === 'JPY' || targetCurrency === 'NGN') {
                return Math.round(converted).toLocaleString();
            } else {
                return converted.toFixed(2);
            }
        }
        
        function initializeCurrency() {
            // Try to detect user's location and set currency
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    (position) => {
                        // In a real app, you'd use a geolocation API to get country
                        // For demo, we'll just use a simple detection
                        detectCurrencyByLocation();
                    },
                    () => {
                        // Fallback to browser language
                        detectCurrencyByLanguage();
                    }
                );
            } else {
                detectCurrencyByLanguage();
            }
            
            // Set up currency change listener
            document.getElementById('currency-selector').addEventListener('change', function() {
                currentCurrency = this.value;
                localStorage.setItem('currency', currentCurrency);
                loadProducts();
                loadFeaturedProducts();
                updateCartDisplay();
                logActivity('Currency Change', `Changed currency to ${currentCurrency}`);
            });
        }
        
        function detectCurrencyByLocation() {
            // This would use a real geolocation API in production
            // For demo, we'll use a simple fallback
            detectCurrencyByLanguage();
        }
        
        function detectCurrencyByLanguage() {
            const language = navigator.language || navigator.userLanguage;
            const savedCurrency = localStorage.getItem('currency');
            
            if (savedCurrency) {
                currentCurrency = savedCurrency;
            } else {
                // Simple language to currency mapping
                const languageToCurrency = {
                    'en-US': 'USD',
                    'en-GB': 'GBP',
                    'en-CA': 'CAD',
                    'en-AU': 'AUD',
                    'de': 'EUR',
                    'fr': 'EUR',
                    'es': 'EUR',
                    'it': 'EUR',
                    'ja': 'JPY',
                    'hi': 'INR',
                    'en-IN': 'INR'
                };
                
                currentCurrency = languageToCurrency[language] || 'USD';
            }
            
            document.getElementById('currency-selector').value = currentCurrency;
        }

        function applyTheme(themeName) {
            const body = document.body;
            const themes = {
                'dark': 'linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%)',
                'blue': 'linear-gradient(135deg, #1e3a8a 0%, #1e40af 100%)',
                'purple': 'linear-gradient(135deg, #581c87 0%, #6b21a8 100%)',
                'green': 'linear-gradient(135deg, #14532d 0%, #166534 100%)'
            };
            
            body.style.background = themes[themeName];
            document.getElementById('current-theme').textContent = `${themeName.charAt(0).toUpperCase() + themeName.slice(1)} Theme`;
            document.getElementById('theme-modified').textContent = new Date().toLocaleString();
            
            alert(`${themeName.charAt(0).toUpperCase() + themeName.slice(1)} theme applied!`);
            logActivity('Theme Change', `Applied ${themeName} theme`);
        }

        function resetBackground() {
            document.body.style.background = '';
            document.body.className = 'gradient-bg text-white min-h-screen';
            document.getElementById('current-theme').textContent = 'Default Dark Theme';
            document.getElementById('theme-modified').textContent = 'Just now';
            
            alert('Background reset to default!');
            logActivity('Theme Reset', 'Reset to default theme');
        }

        // Content Management Functions
        document.getElementById('about-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser || !currentUser.isAdmin) {
                alert('Access denied!');
                return;
            }
            
            const companyName = document.getElementById('company-name').value;
            const tagline = document.getElementById('company-tagline').value;
            const mainDesc = document.getElementById('main-description').value;
            const story = document.getElementById('company-story').value;
            const mission = document.getElementById('mission-statement').value;
            
            // Update the about section content
            updateAboutSection(companyName, tagline, mainDesc, story, mission);
            
            alert('About section updated successfully!');
            logActivity('Content Management', 'Updated About section');
        });

        document.getElementById('contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser || !currentUser.isAdmin) {
                alert('Access denied!');
                return;
            }
            
            const email = document.getElementById('contact-email').value;
            const phone = document.getElementById('contact-phone').value;
            const address = document.getElementById('contact-address').value;
            const hours = document.getElementById('contact-hours').value;
            
            // Update contact information
            updateContactInfo(email, phone, address, hours);
            
            alert('Contact information updated successfully!');
            logActivity('Content Management', 'Updated Contact information');
        });

        function updateAboutSection(name, tagline, mainDesc, story, mission) {
            // Update header
            const headerTitle = document.querySelector('header h1');
            const headerTagline = document.querySelector('header p');
            if (headerTitle) headerTitle.textContent = name;
            if (headerTagline) headerTagline.textContent = tagline;
            
            // Update about section
            const aboutSection = document.getElementById('about');
            if (aboutSection) {
                const title = aboutSection.querySelector('h2');
                const mainDescription = aboutSection.querySelector('.text-xl');
                const storyParagraph = aboutSection.querySelector('.text-gray-400');
                const missionSection = aboutSection.querySelector('.product-card p');
                
                if (title) title.textContent = `ABOUT ${name}`;
                if (mainDescription) mainDescription.textContent = mainDesc;
                if (storyParagraph) storyParagraph.textContent = story;
                if (missionSection) missionSection.textContent = mission;
            }
            
            // Update footer
            const footerTitle = document.querySelector('footer h4');
            const footerTagline = document.querySelector('footer .text-xs');
            if (footerTitle) footerTitle.textContent = name;
            if (footerTagline) footerTagline.textContent = tagline;
        }

        function updateContactInfo(email, phone, address, hours) {
            const contactSection = document.getElementById('contact');
            if (contactSection) {
                const contactItems = contactSection.querySelectorAll('.flex.items-center span:last-child');
                if (contactItems[0]) contactItems[0].textContent = email;
                if (contactItems[1]) contactItems[1].textContent = phone;
                if (contactItems[2]) contactItems[2].textContent = address;
                if (contactItems[3]) contactItems[3].textContent = hours;
            }
        }

        // Enhanced Admin Tab Navigation
        function showAdminTab(tabName) {
            // Update tab buttons
            document.querySelectorAll('.admin-tab-btn').forEach(btn => {
                btn.classList.remove('active', 'bg-orange-500', 'text-white');
                btn.classList.add('bg-gray-700', 'hover:bg-gray-600');
            });
            event.target.classList.add('active', 'bg-orange-500', 'text-white');
            event.target.classList.remove('bg-gray-700', 'hover:bg-gray-600');
            
            // Show selected tab
            document.querySelectorAll('.admin-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            document.getElementById('admin-' + tabName).classList.add('active');
            
            currentAdminTab = tabName;
            
            // Load tab-specific content
            if (tabName === 'security') {
                updateSecurityUI();
                updateSecurityLogs();
            } else if (tabName === 'live-activity') {
                updateLiveActivity();
            } else if (tabName === 'users') {
                updateUsersTable();
            } else if (tabName === 'payments') {
                updatePaymentsTab();
            } else if (tabName === 'products') {
                updateProductManagement();
            } else if (tabName === 'customer-service') {
                updateCustomerMessages();
                updateProductReviews();
                updateResponseTemplatesList();
                updatePaymentReceiversList();
            } else if (tabName === 'attack-monitor') {
                updateAttackMonitor();
            }
        }

        // Enhanced logout function
        function logout() {
            currentUser = null;
            localStorage.removeItem('currentUser');
            updateAuthUI();
            showSection('home');
            logActivity('User Logout', 'User logged out');
        }

        // Image handling functions
        function initializeImageHandlers() {
            // Profile picture handler
            document.getElementById('profile-picture').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const preview = document.getElementById('profile-preview');
                        const placeholder = document.getElementById('profile-placeholder');
                        
                        preview.src = e.target.result;
                        preview.classList.remove('hidden');
                        placeholder.classList.add('hidden');
                    };
                    reader.readAsDataURL(file);
                }
            });

            // Background image handlers
            ['bg-image-1', 'bg-image-2', 'bg-image-3'].forEach(id => {
                document.getElementById(id).addEventListener('change', function(e) {
                    const file = e.target.files[0];
                    if (file) {
                        const reader = new FileReader();
                        reader.onload = function(e) {
                            // Store the image data URL for later use
                            const imageData = e.target.result;
                            // You could preview it here if needed
                            console.log(`Background image ${id} loaded:`, imageData.substring(0, 50) + '...');
                        };
                        reader.readAsDataURL(file);
                    }
                });
            });

            // Product image handlers
            ['product-image-1', 'product-image-2', 'product-image-3'].forEach(id => {
                document.getElementById(id).addEventListener('change', function(e) {
                    const file = e.target.files[0];
                    if (file) {
                        const reader = new FileReader();
                        reader.onload = function(e) {
                            console.log(`Product image ${id} loaded:`, e.target.result.substring(0, 50) + '...');
                        };
                        reader.readAsDataURL(file);
                    }
                });
            });
        }

        // Profile form handler
        document.getElementById('profile-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser) {
                alert('Please login first');
                return;
            }
            
            const email = document.getElementById('profile-email').value;
            const newPassword = document.getElementById('profile-new-password').value;
            const confirmPassword = document.getElementById('profile-confirm-password').value;
            const profilePicture = document.getElementById('profile-picture').files[0];
            
            // Validate password if provided
            if (newPassword && newPassword !== confirmPassword) {
                alert('Passwords do not match!');
                return;
            }
            
            // Update user data
            if (email) currentUser.email = email;
            if (newPassword) currentUser.password = newPassword;
            
            // Handle profile picture
            if (profilePicture) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    currentUser.profilePicture = e.target.result;
                    updateUserAvatar();
                    localStorage.setItem('currentUser', JSON.stringify(currentUser));
                    
                    // Update users array
                    const userIndex = users.findIndex(u => u.id === currentUser.id);
                    if (userIndex !== -1) {
                        users[userIndex] = currentUser;
                        localStorage.setItem('users', JSON.stringify(users));
                    }
                };
                reader.readAsDataURL(profilePicture);
            } else {
                localStorage.setItem('currentUser', JSON.stringify(currentUser));
                const userIndex = users.findIndex(u => u.id === currentUser.id);
                if (userIndex !== -1) {
                    users[userIndex] = currentUser;
                    localStorage.setItem('users', JSON.stringify(users));
                }
            }
            
            hideModal('profile');
            alert('Profile updated successfully!');
            logActivity('Profile Update', 'User updated profile information');
        });

        function updateUserAvatar() {
            const userAvatar = document.getElementById('user-avatar');
            const userAvatarPlaceholder = document.getElementById('user-avatar-placeholder');
            const userInitial = document.getElementById('user-initial');
            
            if (currentUser && currentUser.profilePicture) {
                userAvatar.src = currentUser.profilePicture;
                userAvatar.classList.remove('hidden');
                userAvatarPlaceholder.classList.add('hidden');
            } else if (currentUser) {
                userInitial.textContent = currentUser.username.charAt(0).toUpperCase();
                userAvatar.classList.add('hidden');
                userAvatarPlaceholder.classList.remove('hidden');
            }
        }

        function showModal(modalName) {
            document.getElementById(modalName + '-modal').classList.remove('hidden');
            
            // Pre-populate profile modal if opening profile
            if (modalName === 'profile' && currentUser) {
                document.getElementById('profile-username').value = currentUser.username;
                document.getElementById('profile-email').value = currentUser.email || '';
                
                const profilePreview = document.getElementById('profile-preview');
                const profilePlaceholder = document.getElementById('profile-placeholder');
                const profileInitial = document.getElementById('profile-initial');
                
                if (currentUser.profilePicture) {
                    profilePreview.src = currentUser.profilePicture;
                    profilePreview.classList.remove('hidden');
                    profilePlaceholder.classList.add('hidden');
                } else {
                    profileInitial.textContent = currentUser.username.charAt(0).toUpperCase();
                    profilePreview.classList.add('hidden');
                    profilePlaceholder.classList.remove('hidden');
                }
            }
        }

        // Enhanced updateAuthUI function
        function updateAuthUI() {
            const userMenu = document.getElementById('user-menu');
            const authButtons = document.getElementById('auth-buttons');
            const adminBtn = document.getElementById('admin-btn');
            
            if (currentUser) {
                document.getElementById('user-name').textContent = currentUser.username;
                userMenu.classList.remove('hidden');
                authButtons.classList.add('hidden');
                
                // Update avatar
                updateUserAvatar();
                
                if (currentUser.isAdmin) {
                    adminBtn.classList.remove('hidden');
                }
            } else {
                userMenu.classList.add('hidden');
                authButtons.classList.remove('hidden');
                adminBtn.classList.add('hidden');
            }
        }

        // Enhanced product form handler with image management
        document.getElementById('add-product-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser || !currentUser.isAdmin) {
                alert('Access denied!');
                return;
            }
            
            const name = document.getElementById('product-name').value;
            const price = parseInt(document.getElementById('product-price').value);
            const category = document.getElementById('product-category').value;
            const description = document.getElementById('product-description').value;
            
            const emojis = {
                'tees': '👕',
                'hoodies': '🧥',
                'bottoms': '👖',
                'accessories': '🧢'
            };
            
            const newProduct = {
                id: products.length + 1,
                name: name,
                price: price,
                category: category,
                description: description,
                emoji: emojis[category] || '👕',
                images: []
            };
            
            // Handle product images
            const imageFiles = [
                document.getElementById('product-image-1').files[0],
                document.getElementById('product-image-2').files[0],
                document.getElementById('product-image-3').files[0]
            ].filter(file => file);
            
            if (imageFiles.length > 0) {
                let processedImages = 0;
                const loadingAlert = document.createElement('div');
                loadingAlert.className = 'fixed top-4 right-4 bg-orange-500 text-white px-4 py-2 rounded-lg z-50';
                loadingAlert.textContent = `Processing ${imageFiles.length} images...`;
                document.body.appendChild(loadingAlert);
                
                imageFiles.forEach((file, index) => {
                    // Validate file size (max 5MB)
                    if (file.size > 5 * 1024 * 1024) {
                        alert(`Image ${index + 1} is too large. Please use images under 5MB.`);
                        document.body.removeChild(loadingAlert);
                        return;
                    }
                    
                    // Validate file type
                    if (!file.type.startsWith('image/')) {
                        alert(`File ${index + 1} is not a valid image.`);
                        document.body.removeChild(loadingAlert);
                        return;
                    }
                    
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        // Compress image if needed
                        compressImage(e.target.result, 800, 600, 0.8, (compressedImage) => {
                            newProduct.images.push({
                                id: Date.now() + Math.random(),
                                data: compressedImage,
                                name: file.name,
                                size: file.size,
                                uploadDate: new Date().toISOString()
                            });
                            processedImages++;
                            
                            loadingAlert.textContent = `Processing images... ${processedImages}/${imageFiles.length}`;
                            
                            if (processedImages === imageFiles.length) {
                                // All images processed, add product
                                products.push(newProduct);
                                localStorage.setItem('products', JSON.stringify(products));
                                loadProducts();
                                loadFeaturedProducts();
                                updateAdminStats();
                                updateProductManagement();
                                
                                // Reset form and clear previews
                                document.getElementById('add-product-form').reset();
                                clearImagePreviews();
                                
                                document.body.removeChild(loadingAlert);
                                alert(`Product "${name}" added successfully with ${newProduct.images.length} images!`);
                                logActivity('Product Management', `Added new product with ${newProduct.images.length} images: ${name}`);
                            }
                        });
                    };
                    reader.readAsDataURL(file);
                });
            } else {
                // No images, add product immediately
                products.push(newProduct);
                localStorage.setItem('products', JSON.stringify(products));
                loadProducts();
                loadFeaturedProducts();
                updateAdminStats();
                updateProductManagement();
                
                // Reset form
                this.reset();
                alert(`Product "${name}" added successfully!`);
                logActivity('Product Management', `Added new product: ${name}`);
            }
        });

        // Image compression function
        function compressImage(src, maxWidth, maxHeight, quality, callback) {
            const img = new Image();
            img.onload = function() {
                const canvas = document.createElement('canvas');
                const ctx = canvas.getContext('2d');
                
                // Calculate new dimensions
                let { width, height } = img;
                if (width > height) {
                    if (width > maxWidth) {
                        height = (height * maxWidth) / width;
                        width = maxWidth;
                    }
                } else {
                    if (height > maxHeight) {
                        width = (width * maxHeight) / height;
                        height = maxHeight;
                    }
                }
                
                canvas.width = width;
                canvas.height = height;
                
                // Draw and compress
                ctx.drawImage(img, 0, 0, width, height);
                callback(canvas.toDataURL('image/jpeg', quality));
            };
            img.src = src;
        }

        // Clear image previews
        function clearImagePreviews() {
            ['product-image-1', 'product-image-2', 'product-image-3'].forEach(id => {
                const preview = document.getElementById(id + '-preview');
                if (preview) {
                    preview.style.display = 'none';
                    preview.innerHTML = '';
                }
            });
        }

        // Add image to existing product
        function addImageToProduct(productId) {
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = 'image/*';
            input.multiple = true;
            
            input.onchange = function(e) {
                const files = Array.from(e.target.files);
                const product = products.find(p => p.id === productId);
                
                if (!product) {
                    alert('Product not found!');
                    return;
                }
                
                if (!product.images) product.images = [];
                
                if (product.images.length + files.length > 5) {
                    alert('Maximum 5 images per product allowed!');
                    return;
                }
                
                let processedImages = 0;
                const loadingAlert = document.createElement('div');
                loadingAlert.className = 'fixed top-4 right-4 bg-orange-500 text-white px-4 py-2 rounded-lg z-50';
                loadingAlert.textContent = `Adding ${files.length} images...`;
                document.body.appendChild(loadingAlert);
                
                files.forEach((file, index) => {
                    if (file.size > 5 * 1024 * 1024) {
                        alert(`Image ${index + 1} is too large. Please use images under 5MB.`);
                        return;
                    }
                    
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        compressImage(e.target.result, 800, 600, 0.8, (compressedImage) => {
                            product.images.push({
                                id: Date.now() + Math.random(),
                                data: compressedImage,
                                name: file.name,
                                size: file.size,
                                uploadDate: new Date().toISOString()
                            });
                            processedImages++;
                            
                            if (processedImages === files.length) {
                                localStorage.setItem('products', JSON.stringify(products));
                                loadProducts();
                                loadFeaturedProducts();
                                updateProductManagement();
                                
                                document.body.removeChild(loadingAlert);
                                alert(`${files.length} images added to ${product.name}!`);
                                logActivity('Product Management', `Added ${files.length} images to ${product.name}`);
                            }
                        });
                    };
                    reader.readAsDataURL(file);
                });
            };
            
            input.click();
        }

        // Remove image from product
        function removeImageFromProduct(productId, imageId) {
            const product = products.find(p => p.id === productId);
            if (!product || !product.images) return;
            
            if (confirm('Are you sure you want to remove this image?')) {
                product.images = product.images.filter(img => img.id !== imageId);
                localStorage.setItem('products', JSON.stringify(products));
                loadProducts();
                loadFeaturedProducts();
                updateProductManagement();
                
                alert('Image removed successfully!');
                logActivity('Product Management', `Removed image from ${product.name}`);
            }
        }

        // View product images in modal
        function viewProductImages(productId) {
            const product = products.find(p => p.id === productId);
            if (!product || !product.images || product.images.length === 0) {
                alert('No images found for this product.');
                return;
            }
            
            showProductImageModal(product);
        }

        // Enhanced background application with file support
        function applyBackgroundChanges() {
            const style = document.getElementById('bg-style').value;
            const primaryColor = document.getElementById('primary-color').value;
            const secondaryColor = document.getElementById('secondary-color').value;
            const patternType = document.getElementById('pattern-type').value;
            const enableSlideshow = document.getElementById('enable-slideshow').checked;
            
            const body = document.body;
            const heroSection = document.getElementById('hero-section');
            
            // Clear existing slideshow
            if (slideshowInterval) {
                clearInterval(slideshowInterval);
                slideshowInterval = null;
            }
            
            // Remove existing background classes
            body.className = body.className.replace(/gradient-bg|solid-bg|pattern-bg|image-bg|slideshow-bg/g, '');
            
            switch (style) {
                case 'gradient':
                    body.style.background = `linear-gradient(135deg, ${primaryColor} 0%, ${secondaryColor} 100%)`;
                    heroSection.style.background = 'none';
                    break;
                case 'solid':
                    body.style.background = primaryColor;
                    heroSection.style.background = 'none';
                    break;
                case 'pattern':
                    body.style.background = `linear-gradient(135deg, ${primaryColor} 0%, ${secondaryColor} 100%)`;
                    heroSection.style.background = 'none';
                    break;
                case 'image':
                    const imageFiles = [
                        document.getElementById('bg-image-1').files[0],
                        document.getElementById('bg-image-2').files[0],
                        document.getElementById('bg-image-3').files[0]
                    ].filter(file => file);
                    
                    if (imageFiles.length > 0) {
                        backgroundImages = [];
                        let processedImages = 0;
                        
                        imageFiles.forEach(file => {
                            const reader = new FileReader();
                            reader.onload = function(e) {
                                backgroundImages.push(e.target.result);
                                processedImages++;
                                
                                if (processedImages === imageFiles.length) {
                                    // All images processed
                                    if (enableSlideshow && backgroundImages.length > 1) {
                                        heroSection.classList.add('slideshow-bg');
                                        startHeroSlideshow();
                                    } else {
                                        heroSection.style.backgroundImage = `url('${backgroundImages[0]}')`;
                                        heroSection.style.backgroundSize = 'cover';
                                        heroSection.style.backgroundPosition = 'center';
                                        heroSection.style.backgroundRepeat = 'no-repeat';
                                    }
                                }
                            };
                            reader.readAsDataURL(file);
                        });
                    }
                    break;
            }
            
            document.getElementById('current-theme').textContent = `Custom ${style.charAt(0).toUpperCase() + style.slice(1)} Theme`;
            document.getElementById('theme-modified').textContent = new Date().toLocaleString();
            
            alert('Background updated successfully!');
            logActivity('Theme Customization', `Applied ${style} background theme`);
        }
        
        function startHeroSlideshow() {
            let currentImageIndex = 0;
            const heroSection = document.getElementById('hero-section');
            
            // Set initial image
            heroSection.style.backgroundImage = `url('${backgroundImages[currentImageIndex]}')`;
            heroSection.style.backgroundSize = 'cover';
            heroSection.style.backgroundPosition = 'center';
            heroSection.style.backgroundRepeat = 'no-repeat';
            
            // Start slideshow
            slideshowInterval = setInterval(() => {
                currentImageIndex = (currentImageIndex + 1) % backgroundImages.length;
                heroSection.style.backgroundImage = `url('${backgroundImages[currentImageIndex]}')`;
            }, 10000); // Change every 10 seconds
        }

        // Enhanced security chart initialization
        function initializeCharts() {
            // Sales Chart
            const salesChart = document.getElementById('salesChart');
            if (salesChart) {
                const ctx = salesChart.getContext('2d');
                ctx.fillStyle = '#f97316';
                ctx.fillRect(0, 0, 400, 200);
                ctx.fillStyle = '#ffffff';
                ctx.font = '16px Inter';
                ctx.textAlign = 'center';
                ctx.fillText('Sales Chart (Demo)', 200, 100);
            }
            
            // Active Users Chart
            const activeUsersChart = document.getElementById('activeUsersChart');
            if (activeUsersChart) {
                const ctx = activeUsersChart.getContext('2d');
                ctx.fillStyle = '#10b981';
                ctx.fillRect(0, 0, 300, 150);
                ctx.fillStyle = '#ffffff';
                ctx.font = '14px Inter';
                ctx.textAlign = 'center';
                ctx.fillText('Active Users Chart', 150, 75);
            }
            
            // Page Views Chart
            const pageViewsChart = document.getElementById('pageViewsChart');
            if (pageViewsChart) {
                const ctx = pageViewsChart.getContext('2d');
                ctx.fillStyle = '#3b82f6';
                ctx.fillRect(0, 0, 300, 150);
                ctx.fillStyle = '#ffffff';
                ctx.font = '14px Inter';
                ctx.textAlign = 'center';
                ctx.fillText('Page Views Chart', 150, 75);
            }
            
            // Security Chart
            const securityChart = document.getElementById('securityChart');
            if (securityChart) {
                drawSecurityChart();
                // Update security chart every 5 seconds
                setInterval(drawSecurityChart, 5000);
            }
        }

        function drawSecurityChart() {
            const canvas = document.getElementById('securityChart');
            if (!canvas) return;
            
            const ctx = canvas.getContext('2d');
            const width = canvas.width;
            const height = canvas.height;
            
            // Clear canvas
            ctx.clearRect(0, 0, width, height);
            
            // Draw background
            ctx.fillStyle = '#1f2937';
            ctx.fillRect(0, 0, width, height);
            
            // Draw grid lines
            ctx.strokeStyle = '#374151';
            ctx.lineWidth = 1;
            
            // Vertical lines
            for (let i = 0; i <= 10; i++) {
                const x = (width / 10) * i;
                ctx.beginPath();
                ctx.moveTo(x, 0);
                ctx.lineTo(x, height);
                ctx.stroke();
            }
            
            // Horizontal lines
            for (let i = 0; i <= 5; i++) {
                const y = (height / 5) * i;
                ctx.beginPath();
                ctx.moveTo(0, y);
                ctx.lineTo(width, y);
                ctx.stroke();
            }
            
            // Generate security data points
            const dataPoints = [];
            const currentTime = Date.now();
            for (let i = 0; i < 50; i++) {
                const securityScore = 95 + Math.random() * 5; // 95-100%
                dataPoints.push(securityScore);
            }
            
            // Draw security line
            ctx.strokeStyle = '#10b981';
            ctx.lineWidth = 3;
            ctx.beginPath();
            
            for (let i = 0; i < dataPoints.length; i++) {
                const x = (width / (dataPoints.length - 1)) * i;
                const y = height - ((dataPoints[i] - 90) / 10) * height; // Scale 90-100% to full height
                
                if (i === 0) {
                    ctx.moveTo(x, y);
                } else {
                    ctx.lineTo(x, y);
                }
            }
            ctx.stroke();
            
            // Draw current security score
            ctx.fillStyle = '#10b981';
            ctx.font = 'bold 14px Inter';
            ctx.textAlign = 'left';
            ctx.fillText('Security Score: ' + Math.round(dataPoints[dataPoints.length - 1]) + '%', 10, 25);
            
            // Update security metrics
            document.getElementById('security-score').textContent = Math.round(dataPoints[dataPoints.length - 1]) + '%';
            document.getElementById('active-scans').textContent = Math.floor(Math.random() * 10) + 20;
            document.getElementById('blocked-threats').textContent = Math.floor(Math.random() * 3);
        }

        // Product image modal functions
        function showProductImageModal(product) {
            document.getElementById('product-modal-title').textContent = `${product.name} - Images`;
            const imagesGrid = document.getElementById('product-images-grid');
            
            if (!product.images || product.images.length === 0) {
                imagesGrid.innerHTML = '<p class="text-gray-400 text-center py-8 col-span-full">No images available</p>';
            } else {
                imagesGrid.innerHTML = product.images.map((img, index) => `
                    <div class="relative group cursor-pointer" onclick="selectImage('${img.id}', '${img.name}', '${img.size}', '${img.uploadDate}')">
                        <img src="${img.data || img}" alt="${product.name} ${index + 1}" class="w-full h-48 object-cover rounded-lg border-2 border-gray-700 hover:border-orange-500 transition-colors">
                        <div class="absolute inset-0 bg-black bg-opacity-0 group-hover:bg-opacity-30 transition-all rounded-lg flex items-center justify-center">
                            <div class="opacity-0 group-hover:opacity-100 transition-opacity">
                                <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
                                </svg>
                            </div>
                        </div>
                        <div class="absolute top-2 left-2 bg-black bg-opacity-70 text-white text-xs px-2 py-1 rounded">
                            ${index + 1}
                        </div>
                        ${currentUser && currentUser.isAdmin ? `
                            <button onclick="event.stopPropagation(); removeImageFromProduct(${product.id}, '${img.id}')" class="absolute top-2 right-2 w-6 h-6 bg-red-500 rounded-full text-white text-xs flex items-center justify-center hover:bg-red-600 opacity-0 group-hover:opacity-100 transition-opacity" title="Remove Image">
                                ×
                            </button>
                        ` : ''}
                    </div>
                `).join('');
            }
            
            showModal('product-images');
        }

        function selectImage(imageId, imageName, imageSize, uploadDate) {
            const infoDiv = document.getElementById('selected-image-info');
            const sizeInKB = Math.round(imageSize / 1024);
            const uploadDateFormatted = new Date(uploadDate).toLocaleDateString();
            
            infoDiv.innerHTML = `
                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <p><strong>File Name:</strong> ${imageName}</p>
                        <p><strong>File Size:</strong> ${sizeInKB} KB</p>
                    </div>
                    <div>
                        <p><strong>Upload Date:</strong> ${uploadDateFormatted}</p>
                        <p><strong>Image ID:</strong> ${imageId}</p>
                    </div>
                </div>
            `;
        }

        // Enhanced image handling with previews
        function initializeImageHandlers() {
            // Profile picture handler
            document.getElementById('profile-picture').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const preview = document.getElementById('profile-preview');
                        const placeholder = document.getElementById('profile-placeholder');
                        
                        preview.src = e.target.result;
                        preview.classList.remove('hidden');
                        placeholder.classList.add('hidden');
                    };
                    reader.readAsDataURL(file);
                }
            });

            // Background image handlers
            ['bg-image-1', 'bg-image-2', 'bg-image-3'].forEach(id => {
                document.getElementById(id).addEventListener('change', function(e) {
                    const file = e.target.files[0];
                    if (file) {
                        const reader = new FileReader();
                        reader.onload = function(e) {
                            console.log(`Background image ${id} loaded:`, file.name);
                        };
                        reader.readAsDataURL(file);
                    }
                });
            });

            // Product image handlers with previews
            ['product-image-1', 'product-image-2', 'product-image-3'].forEach((id, index) => {
                const input = document.getElementById(id);
                input.addEventListener('change', function(e) {
                    const file = e.target.files[0];
                    if (file) {
                        // Validate file
                        if (file.size > 5 * 1024 * 1024) {
                            alert('Image is too large. Please use images under 5MB.');
                            this.value = '';
                            return;
                        }
                        
                        if (!file.type.startsWith('image/')) {
                            alert('Please select a valid image file.');
                            this.value = '';
                            return;
                        }
                        
                        // Create preview
                        const reader = new FileReader();
                        reader.onload = function(e) {
                            showImagePreview(id, e.target.result, file.name);
                        };
                        reader.readAsDataURL(file);
                    } else {
                        hideImagePreview(id);
                    }
                });
            });
        }

        function showImagePreview(inputId, imageSrc, fileName) {
            let previewContainer = document.getElementById(inputId + '-preview');
            
            if (!previewContainer) {
                previewContainer = document.createElement('div');
                previewContainer.id = inputId + '-preview';
                previewContainer.className = 'mt-2 relative';
                document.getElementById(inputId).parentNode.appendChild(previewContainer);
            }
            
            previewContainer.innerHTML = `
                <div class="relative inline-block">
                    <img src="${imageSrc}" alt="Preview" class="w-20 h-20 object-cover rounded border border-gray-600">
                    <button type="button" onclick="clearImageInput('${inputId}')" class="absolute -top-1 -right-1 w-5 h-5 bg-red-500 rounded-full text-white text-xs flex items-center justify-center hover:bg-red-600">×</button>
                    <p class="text-xs text-gray-400 mt-1 max-w-20 truncate">${fileName}</p>
                </div>
            `;
            previewContainer.style.display = 'block';
        }

        function hideImagePreview(inputId) {
            const previewContainer = document.getElementById(inputId + '-preview');
            if (previewContainer) {
                previewContainer.style.display = 'none';
            }
        }

        function clearImageInput(inputId) {
            document.getElementById(inputId).value = '';
            hideImagePreview(inputId);
        }

        // Enhanced signup with data persistence
        document.getElementById('signup-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('signup-username').value;
            const email = document.getElementById('signup-email').value;
            const password = document.getElementById('signup-password').value;
            const confirmPassword = document.getElementById('signup-confirm-password').value;
            
            if (password !== confirmPassword) {
                alert('Passwords do not match!');
                return;
            }
            
            if (users.find(u => u.username === username || u.email === email)) {
                alert('Username or email already exists!');
                return;
            }
            
            const newUser = {
                id: users.length + 1,
                username: username,
                email: email,
                password: password,
                isAdmin: username === 'admin' || users.length === 0, // First user or 'admin' username is admin
                joinedDate: new Date().toISOString(),
                status: 'active'
            };
            
            users.push(newUser);
            currentUser = newUser;
            
            // Store data persistently
            localStorage.setItem('users', JSON.stringify(users));
            localStorage.setItem('currentUser', JSON.stringify(newUser));
            
            updateAuthUI();
            hideModal('signup');
            alert('Account created successfully!');
            updateAdminStats();
            logActivity('User Registration', 'New user signed up');
            logSecurityEvent('New User Registration', `User ${username} registered`);
        });

        // Payment Receiver Management
        document.getElementById('payment-receiver-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser || !currentUser.isAdmin) {
                alert('Access denied!');
                return;
            }
            
            const receiver = {
                id: paymentReceivers.length + 1,
                type: document.getElementById('payment-type').value,
                name: document.getElementById('receiver-name').value,
                details: document.getElementById('receiver-details').value,
                currency: document.getElementById('receiver-currency').value,
                country: document.getElementById('receiver-country').value,
                notes: document.getElementById('receiver-notes').value,
                autoProcess: document.getElementById('auto-process').checked,
                status: 'active',
                dateAdded: new Date().toISOString()
            };
            
            paymentReceivers.push(receiver);
            localStorage.setItem('paymentReceivers', JSON.stringify(paymentReceivers));
            
            updatePaymentReceiversList();
            this.reset();
            alert('Payment receiver added successfully!');
            logActivity('Payment Management', `Added ${receiver.type} payment receiver`);
        });

        // Customer Service Form
        document.getElementById('customer-service-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser) {
                alert('Please login to send a message');
                return;
            }
            
            const message = {
                id: customerMessages.length + 1,
                customerId: currentUser.id,
                customerName: currentUser.username,
                customerEmail: currentUser.email,
                subject: document.getElementById('support-subject').value,
                orderNumber: document.getElementById('support-order-number').value,
                message: document.getElementById('support-message').value,
                priority: document.getElementById('support-priority').value,
                status: 'unread',
                timestamp: new Date().toISOString(),
                responses: []
            };
            
            customerMessages.unshift(message);
            localStorage.setItem('customerMessages', JSON.stringify(customerMessages));
            
            updateCustomerMessagesCount();
            hideModal('customer-service');
            this.reset();
            alert('Your message has been sent! Our team will respond shortly.');
            logActivity('Customer Service', 'Sent support message');
        });

        // Contact Page Form
        document.getElementById('contact-page-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const message = {
                id: customerMessages.length + 1,
                customerId: currentUser ? currentUser.id : null,
                customerName: document.getElementById('contact-name').value,
                customerEmail: document.getElementById('contact-email-field').value,
                subject: document.getElementById('contact-subject').value,
                orderNumber: null,
                message: document.getElementById('contact-message-field').value,
                priority: 'medium',
                status: 'unread',
                timestamp: new Date().toISOString(),
                responses: []
            };
            
            customerMessages.unshift(message);
            localStorage.setItem('customerMessages', JSON.stringify(customerMessages));
            
            updateCustomerMessagesCount();
            this.reset();
            alert('Your message has been sent! We will get back to you soon.');
            logActivity('Contact Form', 'Sent contact message');
        });

        // Product Rating Form
        document.getElementById('product-rating-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser) {
                alert('Please login to submit a review');
                return;
            }
            
            if (selectedRating === 0) {
                alert('Please select a rating');
                return;
            }
            
            const review = {
                id: productReviews.length + 1,
                productId: currentRatingProduct.id,
                productName: currentRatingProduct.name,
                customerId: currentUser.id,
                customerName: currentUser.username,
                rating: selectedRating,
                title: document.getElementById('review-title').value,
                comment: document.getElementById('review-comment').value,
                recommend: document.getElementById('recommend-product').checked,
                timestamp: new Date().toISOString(),
                status: 'approved'
            };
            
            productReviews.push(review);
            localStorage.setItem('productReviews', JSON.stringify(productReviews));
            
            // Update product rating
            updateProductRating(currentRatingProduct.id);
            
            hideModal('product-rating');
            this.reset();
            selectedRating = 0;
            updateStarDisplay();
            
            alert('Thank you for your review!');
            logActivity('Product Review', `Reviewed ${currentRatingProduct.name}`);
        });

        // Response Template Form
        document.getElementById('response-template-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser || !currentUser.isAdmin) {
                alert('Access denied!');
                return;
            }
            
            const template = {
                id: responseTemplates.length + 1,
                name: document.getElementById('template-name').value,
                content: document.getElementById('template-content').value,
                dateCreated: new Date().toISOString()
            };
            
            responseTemplates.push(template);
            localStorage.setItem('responseTemplates', JSON.stringify(responseTemplates));
            
            updateResponseTemplatesList();
            this.reset();
            alert('Response template added successfully!');
        });

        // Rating System Functions
        function initializeRatingSystem() {
            const starButtons = document.querySelectorAll('.star-rating');
            starButtons.forEach(star => {
                star.addEventListener('click', function() {
                    selectedRating = parseInt(this.dataset.rating);
                    updateStarDisplay();
                });
                
                star.addEventListener('mouseenter', function() {
                    const rating = parseInt(this.dataset.rating);
                    highlightStars(rating);
                });
            });
            
            document.querySelector('.star-rating').parentElement.addEventListener('mouseleave', function() {
                updateStarDisplay();
            });
        }

        function updateStarDisplay() {
            const starButtons = document.querySelectorAll('.star-rating');
            const ratingText = document.getElementById('rating-text');
            
            starButtons.forEach((star, index) => {
                if (index < selectedRating) {
                    star.classList.remove('text-gray-400');
                    star.classList.add('text-yellow-500');
                } else {
                    star.classList.remove('text-yellow-500');
                    star.classList.add('text-gray-400');
                }
            });
            
            const ratingTexts = ['', 'Poor', 'Fair', 'Good', 'Very Good', 'Excellent'];
            ratingText.textContent = selectedRating > 0 ? ratingTexts[selectedRating] : 'Click stars to rate';
        }

        function highlightStars(rating) {
            const starButtons = document.querySelectorAll('.star-rating');
            starButtons.forEach((star, index) => {
                if (index < rating) {
                    star.classList.remove('text-gray-400');
                    star.classList.add('text-yellow-500');
                } else {
                    star.classList.remove('text-yellow-500');
                    star.classList.add('text-gray-400');
                }
            });
        }

        function showRatingModal(productId) {
            if (!currentUser) {
                alert('Please login to rate products');
                showModal('login');
                return;
            }
            
            currentRatingProduct = products.find(p => p.id === productId);
            if (!currentRatingProduct) return;
            
            document.getElementById('rating-product-name').textContent = currentRatingProduct.name;
            selectedRating = 0;
            updateStarDisplay();
            showModal('product-rating');
        }

        function updateProductRating(productId) {
            const productReviewsForProduct = productReviews.filter(r => r.productId === productId);
            const product = products.find(p => p.id === productId);
            
            if (product && productReviewsForProduct.length > 0) {
                const totalRating = productReviewsForProduct.reduce((sum, review) => sum + review.rating, 0);
                product.averageRating = totalRating / productReviewsForProduct.length;
                product.reviewCount = productReviewsForProduct.length;
                
                localStorage.setItem('products', JSON.stringify(products));
                loadProducts();
                loadFeaturedProducts();
            }
        }

        // Customer Service Functions
        function initializeCustomerService() {
            updateCustomerMessagesCount();
        }

        function updateCustomerMessagesCount() {
            const unreadCount = customerMessages.filter(m => m.status === 'unread').length;
            const unreadElement = document.getElementById('unread-messages');
            if (unreadElement) {
                unreadElement.textContent = `${unreadCount} Unread`;
            }
        }

        function updateCustomerMessages() {
            const messagesContainer = document.getElementById('customer-messages');
            if (!messagesContainer) return;
            
            if (customerMessages.length === 0) {
                messagesContainer.innerHTML = '<p class="text-gray-400 text-center py-8">No customer messages</p>';
                return;
            }
            
            messagesContainer.innerHTML = customerMessages.map(message => `
                <div class="bg-gray-800 p-4 rounded-lg ${message.status === 'unread' ? 'border-l-4 border-orange-500' : ''}">
                    <div class="flex justify-between items-start mb-3">
                        <div>
                            <h5 class="font-bold">${message.customerName}</h5>
                            <p class="text-sm text-gray-400">${message.customerEmail}</p>
                            <p class="text-xs text-gray-500">${new Date(message.timestamp).toLocaleString()}</p>
                        </div>
                        <div class="flex items-center space-x-2">
                            <span class="px-2 py-1 rounded text-xs ${getPriorityColor(message.priority)}">${message.priority.toUpperCase()}</span>
                            <span class="px-2 py-1 rounded text-xs ${message.status === 'unread' ? 'bg-orange-600' : 'bg-green-600'}">${message.status.toUpperCase()}</span>
                        </div>
                    </div>
                    <div class="mb-3">
                        <p class="text-sm font-medium">${message.subject}</p>
                        ${message.orderNumber ? `<p class="text-xs text-gray-400">Order: ${message.orderNumber}</p>` : ''}
                        <p class="text-sm text-gray-300 mt-2">${message.message}</p>
                    </div>
                    <div class="flex space-x-2">
                        <button onclick="markAsRead(${message.id})" class="bg-blue-600 hover:bg-blue-700 px-3 py-1 rounded text-xs">Mark Read</button>
                        <button onclick="respondToMessage(${message.id})" class="bg-green-600 hover:bg-green-700 px-3 py-1 rounded text-xs">Respond</button>
                        <button onclick="deleteMessage(${message.id})" class="bg-red-600 hover:bg-red-700 px-3 py-1 rounded text-xs">Delete</button>
                    </div>
                </div>
            `).join('');
        }

        function updateProductReviews() {
            const reviewsContainer = document.getElementById('product-reviews');
            if (!reviewsContainer) return;
            
            if (productReviews.length === 0) {
                reviewsContainer.innerHTML = '<p class="text-gray-400 text-center py-8">No product reviews yet</p>';
                return;
            }
            
            reviewsContainer.innerHTML = productReviews.map(review => `
                <div class="bg-gray-800 p-4 rounded-lg">
                    <div class="flex justify-between items-start mb-3">
                        <div>
                            <h5 class="font-bold">${review.productName}</h5>
                            <p class="text-sm text-gray-400">by ${review.customerName}</p>
                            <div class="flex items-center space-x-2 mt-1">
                                <div class="flex text-yellow-500">
                                    ${'★'.repeat(review.rating)}${'☆'.repeat(5 - review.rating)}
                                </div>
                                <span class="text-xs text-gray-400">${new Date(review.timestamp).toLocaleDateString()}</span>
                            </div>
                        </div>
                        ${review.recommend ? '<span class="text-green-500 text-xs">👍 Recommended</span>' : ''}
                    </div>
                    <div>
                        <p class="font-medium text-sm">${review.title}</p>
                        <p class="text-sm text-gray-300 mt-1">${review.comment}</p>
                    </div>
                </div>
            `).join('');
        }

        function updatePaymentReceiversList() {
            const receiversList = document.getElementById('payment-receivers-list');
            if (!receiversList) return;
            
            if (paymentReceivers.length === 0) {
                receiversList.innerHTML = '<p class="text-gray-400 text-center py-8">No payment receivers configured</p>';
                return;
            }
            
            receiversList.innerHTML = paymentReceivers.map(receiver => `
                <div class="bg-gray-800 p-3 rounded-lg">
                    <div class="flex justify-between items-start">
                        <div class="flex-1">
                            <p class="font-medium">${receiver.name}</p>
                            <p class="text-sm text-gray-400">${receiver.type.toUpperCase()} - ${receiver.currency}</p>
                            <p class="text-xs text-gray-500">${receiver.details}</p>
                            ${receiver.autoProcess ? '<span class="text-xs text-green-500">🤖 Auto-process enabled</span>' : ''}
                        </div>
                        <div class="flex space-x-1">
                            <button onclick="toggleReceiver(${receiver.id})" class="bg-orange-600 hover:bg-orange-700 px-2 py-1 rounded text-xs">
                                ${receiver.status === 'active' ? 'Disable' : 'Enable'}
                            </button>
                            <button onclick="removeReceiver(${receiver.id})" class="bg-red-600 hover:bg-red-700 px-2 py-1 rounded text-xs">Remove</button>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        function updateResponseTemplatesList() {
            const templatesList = document.getElementById('response-templates');
            if (!templatesList) return;
            
            if (responseTemplates.length === 0) {
                templatesList.innerHTML = '<p class="text-gray-400 text-center py-8">No templates saved</p>';
                return;
            }
            
            templatesList.innerHTML = responseTemplates.map(template => `
                <div class="bg-gray-800 p-3 rounded-lg">
                    <div class="flex justify-between items-start">
                        <div class="flex-1">
                            <p class="font-medium text-sm">${template.name}</p>
                            <p class="text-xs text-gray-400">${template.content.substring(0, 50)}...</p>
                        </div>
                        <div class="flex space-x-1">
                            <button onclick="useTemplate(${template.id})" class="bg-blue-600 hover:bg-blue-700 px-2 py-1 rounded text-xs">Use</button>
                            <button onclick="deleteTemplate(${template.id})" class="bg-red-600 hover:bg-red-700 px-2 py-1 rounded text-xs">Delete</button>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // Utility Functions
        function getPriorityColor(priority) {
            const colors = {
                'low': 'bg-gray-600',
                'medium': 'bg-blue-600',
                'high': 'bg-orange-600',
                'critical': 'bg-red-600'
            };
            return colors[priority] || 'bg-gray-600';
        }

        function markAsRead(messageId) {
            const message = customerMessages.find(m => m.id === messageId);
            if (message) {
                message.status = 'read';
                localStorage.setItem('customerMessages', JSON.stringify(customerMessages));
                updateCustomerMessages();
                updateCustomerMessagesCount();
            }
        }

        function respondToMessage(messageId) {
            // This would open a response modal in a full implementation
            const response = prompt('Enter your response:');
            if (response) {
                const message = customerMessages.find(m => m.id === messageId);
                if (message) {
                    message.responses.push({
                        id: Date.now(),
                        adminId: currentUser.id,
                        adminName: currentUser.username,
                        response: response,
                        timestamp: new Date().toISOString()
                    });
                    message.status = 'responded';
                    localStorage.setItem('customerMessages', JSON.stringify(customerMessages));
                    updateCustomerMessages();
                    alert('Response sent!');
                }
            }
        }

        function deleteMessage(messageId) {
            if (confirm('Are you sure you want to delete this message?')) {
                customerMessages = customerMessages.filter(m => m.id !== messageId);
                localStorage.setItem('customerMessages', JSON.stringify(customerMessages));
                updateCustomerMessages();
                updateCustomerMessagesCount();
            }
        }

        function toggleReceiver(receiverId) {
            const receiver = paymentReceivers.find(r => r.id === receiverId);
            if (receiver) {
                receiver.status = receiver.status === 'active' ? 'inactive' : 'active';
                localStorage.setItem('paymentReceivers', JSON.stringify(paymentReceivers));
                updatePaymentReceiversList();
            }
        }

        function removeReceiver(receiverId) {
            if (confirm('Are you sure you want to remove this payment receiver?')) {
                paymentReceivers = paymentReceivers.filter(r => r.id !== receiverId);
                localStorage.setItem('paymentReceivers', JSON.stringify(paymentReceivers));
                updatePaymentReceiversList();
            }
        }

        function useTemplate(templateId) {
            const template = responseTemplates.find(t => t.id === templateId);
            if (template) {
                // This would populate a response field in a full implementation
                alert(`Template "${template.name}" selected:\n\n${template.content}`);
            }
        }

        function deleteTemplate(templateId) {
            if (confirm('Are you sure you want to delete this template?')) {
                responseTemplates = responseTemplates.filter(t => t.id !== templateId);
                localStorage.setItem('responseTemplates', JSON.stringify(responseTemplates));
                updateResponseTemplatesList();
            }
        }

        function populateCurrencyOptions() {
            const currencySelectors = ['currency-selector', 'receiver-currency'];
            
            currencySelectors.forEach(selectorId => {
                const selector = document.getElementById(selectorId);
                if (selector) {
                    // Clear existing options except the first one
                    while (selector.children.length > 1) {
                        selector.removeChild(selector.lastChild);
                    }
                    
                    // Add all currencies
                    Object.keys(exchangeRates).forEach(currency => {
                        const option = document.createElement('option');
                        option.value = currency;
                        option.textContent = `${currency} - ${currencySymbols[currency]}`;
                        selector.appendChild(option);
                    });
                }
            });
        }

        function loadStoredData() {
            // Load stored data from localStorage
            const storedPaymentReceivers = localStorage.getItem('paymentReceivers');
            const storedCustomerMessages = localStorage.getItem('customerMessages');
            const storedProductReviews = localStorage.getItem('productReviews');
            const storedResponseTemplates = localStorage.getItem('responseTemplates');
            
            if (storedPaymentReceivers) {
                paymentReceivers = JSON.parse(storedPaymentReceivers);
            }
            
            if (storedCustomerMessages) {
                customerMessages = JSON.parse(storedCustomerMessages);
            }
            
            if (storedProductReviews) {
                productReviews = JSON.parse(storedProductReviews);
            }
            
            if (storedResponseTemplates) {
                responseTemplates = JSON.parse(storedResponseTemplates);
            }
        }

        // Attack Monitor Functions
        function updateAttackMonitor() {
            const attackAttempts = JSON.parse(localStorage.getItem('attackAttempts') || '[]');
            const today = new Date().toDateString();
            
            // Update statistics
            document.getElementById('total-attacks').textContent = attackAttempts.length;
            document.getElementById('today-attacks').textContent = attackAttempts.filter(a => new Date(a.timestamp).toDateString() === today).length;
            document.getElementById('code-attacks').textContent = attackAttempts.filter(a => a.type.includes('Developer Tools') || a.type.includes('Code')).length;
            document.getElementById('rightclick-attacks').textContent = attackAttempts.filter(a => a.type.includes('Context Menu')).length;
            
            // Update attack feed
            updateAttackFeed(attackAttempts);
            
            // Update attack details table
            updateAttackDetailsTable(attackAttempts);
            
            // Update last scan time
            document.getElementById('last-security-scan').textContent = new Date().toLocaleString();
        }

        function updateAttackFeed(attackAttempts) {
            const attackFeed = document.getElementById('attack-feed');
            if (!attackFeed) return;
            
            if (attackAttempts.length === 0) {
                attackFeed.innerHTML = '<p class="text-gray-400 text-center py-8">No attack attempts detected</p>';
                return;
            }
            
            attackFeed.innerHTML = attackAttempts.slice(0, 10).map(attack => `
                <div class="bg-red-900/30 border border-red-500/30 p-4 rounded-lg">
                    <div class="flex justify-between items-start mb-2">
                        <div>
                            <h5 class="font-bold text-red-400">${attack.type}</h5>
                            <p class="text-sm text-red-300">${attack.details}</p>
                        </div>
                        <span class="px-2 py-1 rounded text-xs bg-red-600 text-white">${attack.severity}</span>
                    </div>
                    <div class="text-xs text-gray-400">
                        <p>Time: ${new Date(attack.timestamp).toLocaleString()}</p>
                        <p>Location: ${attack.location}</p>
                        <p>User Agent: ${attack.userAgent.substring(0, 50)}...</p>
                    </div>
                </div>
            `).join('');
        }

        function updateAttackDetailsTable(attackAttempts) {
            const attackTable = document.getElementById('attack-details-table');
            if (!attackTable) return;
            
            if (attackAttempts.length === 0) {
                attackTable.innerHTML = '<tr><td colspan="6" class="text-center text-gray-400 py-8">No attack attempts recorded</td></tr>';
                return;
            }
            
            attackTable.innerHTML = attackAttempts.map(attack => `
                <tr class="border-b border-gray-700">
                    <td class="py-3">${new Date(attack.timestamp).toLocaleString()}</td>
                    <td class="py-3">
                        <span class="px-2 py-1 rounded text-xs bg-red-600">${attack.type}</span>
                    </td>
                    <td class="py-3 max-w-xs truncate">${attack.details}</td>
                    <td class="py-3">${attack.location}</td>
                    <td class="py-3 max-w-xs truncate">${attack.userAgent}</td>
                    <td class="py-3">
                        <span class="px-2 py-1 rounded text-xs ${attack.severity === 'HIGH' ? 'bg-red-600' : 'bg-orange-600'}">${attack.severity}</span>
                    </td>
                </tr>
            `).join('');
        }

        function clearAttackLogs() {
            if (confirm('Are you sure you want to clear all attack logs? This action cannot be undone.')) {
                localStorage.removeItem('attackAttempts');
                updateAttackMonitor();
                alert('Attack logs cleared successfully!');
                logActivity('Security Management', 'Cleared attack logs');
            }
        }

        function exportAttackData() {
            const attackAttempts = JSON.parse(localStorage.getItem('attackAttempts') || '[]');
            if (attackAttempts.length === 0) {
                alert('No attack data to export');
                return;
            }
            
            const csvContent = "data:text/csv;charset=utf-8," + 
                "Time,Attack Type,Details,Location,User Agent,Severity\n" +
                attackAttempts.map(attack => 
                    `"${new Date(attack.timestamp).toLocaleString()}","${attack.type}","${attack.details}","${attack.location}","${attack.userAgent}","${attack.severity}"`
                ).join('\n');
            
            const encodedUri = encodeURI(csvContent);
            const link = document.createElement('a');
            link.setAttribute('href', encodedUri);
            link.setAttribute('download', `attack_logs_${new Date().toISOString().split('T')[0]}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            
            alert('Attack data exported successfully!');
            logActivity('Security Management', 'Exported attack data');
        }

        function blockSuspiciousIPs() {
            // This would implement IP blocking in a real application
            alert('🚫 IP Blocking Feature\n\nThis feature would block suspicious IP addresses in a production environment. For demo purposes, this shows the interface only.');
            logActivity('Security Management', 'Attempted IP blocking (demo)');
        }
        // Admin Delivery Tracking Functions
        function updateDeliveryTracking() {
            updateDeliveryStats();
            updateActiveShipmentsList();
            updateDeliveryAlerts();
            updateAdminDeliveryMap();
            drawDeliveryChart();
        }

        function updateDeliveryStats() {
            const activeShipments = shipments.filter(s => s.status !== 'delivered').length;
            const deliveredToday = shipments.filter(s => {
                if (s.actualDelivery) {
                    const deliveryDate = new Date(s.actualDelivery).toDateString();
                    const today = new Date().toDateString();
                    return deliveryDate === today;
                }
                return false;
            }).length;
            const inTransit = shipments.filter(s => s.status === 'in_transit' || s.status === 'out_for_delivery').length;
            const delayed = shipments.filter(s => s.status === 'delayed').length;

            document.getElementById('active-shipments').textContent = activeShipments;
            document.getElementById('delivered-today').textContent = deliveredToday;
            document.getElementById('in-transit').textContent = inTransit;
            document.getElementById('delayed-shipments').textContent = delayed;
        }

        function updateActiveShipmentsList() {
            const shipmentsList = document.getElementById('active-shipments-list');
            const activeShipments = shipments.filter(s => s.status !== 'delivered');

            if (activeShipments.length === 0) {
                shipmentsList.innerHTML = '<p class="text-gray-400 text-center py-8">No active shipments</p>';
                return;
            }

            shipmentsList.innerHTML = activeShipments.map(shipment => {
                const statusConfig = getStatusConfig(shipment.status);
                return `
                    <div class="bg-gray-800 p-4 rounded-lg border-l-4 ${getStatusBorderColor(shipment.status)}">
                        <div class="flex justify-between items-start mb-3">
                            <div>
                                <h5 class="font-bold">${shipment.orderId}</h5>
                                <p class="text-sm text-gray-400">${shipment.customerName}</p>
                                <p class="text-xs text-gray-500">${shipment.items.join(', ')}</p>
                            </div>
                            <div class="text-right">
                                <span class="px-2 py-1 rounded text-xs ${statusConfig.class}">${statusConfig.text}</span>
                                <p class="text-xs text-gray-400 mt-1">${shipment.id}</p>
                            </div>
                        </div>
                        <div class="flex justify-between items-center text-sm">
                            <div>
                                <p class="text-gray-400">📍 ${shipment.currentLocation.name}</p>
                                <p class="text-gray-500">🎯 ${getNextLocation(shipment)}</p>
                            </div>
                            <div class="flex space-x-2">
                                <button onclick="viewShipmentDetails('${shipment.id}')" class="bg-blue-600 hover:bg-blue-700 px-2 py-1 rounded text-xs">
                                    👁️ View
                                </button>
                                <button onclick="updateShipmentStatus('${shipment.id}')" class="bg-orange-600 hover:bg-orange-700 px-2 py-1 rounded text-xs">
                                    📝 Update
                                </button>
                            </div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function getStatusBorderColor(status) {
            const colors = {
                'pending': 'border-gray-500',
                'picked_up': 'border-blue-500',
                'in_transit': 'border-orange-500',
                'out_for_delivery': 'border-green-500',
                'delivered': 'border-green-700',
                'delayed': 'border-red-500',
                'exception': 'border-red-700'
            };
            return colors[status] || 'border-gray-500';
        }

        function updateDeliveryAlerts() {
            const alertsContainer = document.getElementById('delivery-alerts');
            
            // Generate sample alerts
            const alerts = [
                {
                    id: 1,
                    type: 'delay',
                    message: 'Shipment HE123456789US is experiencing weather delays',
                    severity: 'medium',
                    timestamp: new Date(Date.now() - 2 * 60 * 60 * 1000) // 2 hours ago
                },
                {
                    id: 2,
                    type: 'exception',
                    message: 'Address verification needed for shipment HE987654321US',
                    severity: 'high',
                    timestamp: new Date(Date.now() - 30 * 60 * 1000) // 30 minutes ago
                }
            ];

            if (alerts.length === 0) {
                alertsContainer.innerHTML = '<p class="text-gray-400 text-center py-8">No delivery alerts</p>';
                return;
            }

            alertsContainer.innerHTML = alerts.map(alert => {
                const severityColors = {
                    'low': 'border-yellow-500 bg-yellow-900/20',
                    'medium': 'border-orange-500 bg-orange-900/20',
                    'high': 'border-red-500 bg-red-900/20'
                };

                return `
                    <div class="p-4 rounded-lg border ${severityColors[alert.severity]}">
                        <div class="flex justify-between items-start">
                            <div class="flex-1">
                                <div class="flex items-center space-x-2 mb-2">
                                    <span class="text-lg">${alert.type === 'delay' ? '⏰' : '⚠️'}</span>
                                    <span class="font-medium text-${alert.severity === 'high' ? 'red' : alert.severity === 'medium' ? 'orange' : 'yellow'}-400">
                                        ${alert.type.toUpperCase()}
                                    </span>
                                </div>
                                <p class="text-sm text-gray-300">${alert.message}</p>
                                <p class="text-xs text-gray-500 mt-1">${alert.timestamp.toLocaleString()}</p>
                            </div>
                            <div class="flex space-x-2">
                                <button onclick="resolveAlert(${alert.id})" class="bg-green-600 hover:bg-green-700 px-2 py-1 rounded text-xs">
                                    ✓ Resolve
                                </button>
                                <button onclick="dismissAlert(${alert.id})" class="bg-gray-600 hover:bg-gray-700 px-2 py-1 rounded text-xs">
                                    ✕ Dismiss
                                </button>
                            </div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function updateAdminDeliveryMap() {
            const mapContainer = document.getElementById('admin-delivery-map');
            
            // Create an interactive admin map with all shipments
            mapContainer.innerHTML = `
                <div class="absolute inset-0 bg-gradient-to-br from-gray-900 to-blue-900 opacity-30"></div>
                <div class="absolute inset-0">
                    <!-- US Map Background -->
                    <svg class="w-full h-full" viewBox="0 0 800 400" style="background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);">
                        <!-- Simplified US outline -->
                        <path d="M 100 200 L 200 180 L 300 160 L 400 170 L 500 160 L 600 180 L 700 200 L 680 250 L 600 280 L 500 290 L 400 280 L 300 270 L 200 260 L 120 240 Z" 
                              fill="rgba(55, 65, 81, 0.3)" stroke="rgba(75, 85, 99, 0.5)" stroke-width="2"/>
                        
                        <!-- Major cities -->
                        <circle cx="150" cy="220" r="3" fill="#3b82f6" opacity="0.7"/>
                        <text x="155" y="225" fill="#94a3b8" font-size="10">NYC</text>
                        
                        <circle cx="120" cy="280" r="3" fill="#3b82f6" opacity="0.7"/>
                        <text x="125" y="285" fill="#94a3b8" font-size="10">Miami</text>
                        
                        <circle cx="300" cy="240" r="3" fill="#3b82f6" opacity="0.7"/>
                        <text x="305" y="245" fill="#94a3b8" font-size="10">Chicago</text>
                        
                        <circle cx="200" cy="280" r="3" fill="#3b82f6" opacity="0.7"/>
                        <text x="205" y="285" fill="#94a3b8" font-size="10">Dallas</text>
                        
                        <circle cx="500" cy="250" r="3" fill="#3b82f6" opacity="0.7"/>
                        <text x="505" y="255" fill="#94a3b8" font-size="10">Denver</text>
                        
                        <circle cx="600" cy="220" r="3" fill="#3b82f6" opacity="0.7"/>
                        <text x="605" y="225" fill="#94a3b8" font-size="10">LA</text>
                        
                        <!-- Active shipment routes -->
                        ${shipments.filter(s => s.status !== 'delivered').map((shipment, index) => {
                            const startX = 150 + (index * 100);
                            const startY = 200 + (index * 20);
                            const endX = 600 - (index * 80);
                            const endY = 220 + (index * 15);
                            
                            return `
                                <line x1="${startX}" y1="${startY}" x2="${endX}" y2="${endY}" 
                                      stroke="${shipment.status === 'out_for_delivery' ? '#10b981' : '#f59e0b'}" 
                                      stroke-width="2" stroke-dasharray="5,5" opacity="0.8">
                                    <animate attributeName="stroke-dashoffset" values="0;-10" dur="2s" repeatCount="indefinite"/>
                                </line>
                                
                                <!-- Moving truck -->
                                <g transform="translate(${startX + (endX - startX) * 0.6}, ${startY + (endY - startY) * 0.6})">
                                    <circle r="8" fill="rgba(0,0,0,0.5)"/>
                                    <text text-anchor="middle" dy="4" font-size="12">🚚</text>
                                    <animateTransform attributeName="transform" 
                                                    type="translate" 
                                                    values="${startX},${startY};${endX},${endY};${startX},${startY}" 
                                                    dur="${10 + index * 2}s" 
                                                    repeatCount="indefinite"/>
                                </g>
                            `;
                        }).join('')}
                        
                        <!-- Delivery markers -->
                        ${shipments.map((shipment, index) => {
                            const x = 150 + (index * 120);
                            const y = 200 + (Math.sin(index) * 50);
                            const color = shipment.status === 'delivered' ? '#10b981' : 
                                         shipment.status === 'out_for_delivery' ? '#f59e0b' : '#ef4444';
                            
                            return `
                                <circle cx="${x}" cy="${y}" r="6" fill="${color}" opacity="0.9" class="cursor-pointer">
                                    <animate attributeName="r" values="6;8;6" dur="2s" repeatCount="indefinite"/>
                                </circle>
                                <text x="${x}" y="${y - 12}" text-anchor="middle" fill="#e2e8f0" font-size="8">${shipment.orderId}</text>
                            `;
                        }).join('')}
                    </svg>
                </div>
                
                <!-- Map legend -->
                <div class="absolute top-4 left-4 bg-black bg-opacity-70 text-white p-3 rounded-lg text-xs">
                    <h4 class="font-bold mb-2">Live Shipments</h4>
                    <div class="space-y-1">
                        <div class="flex items-center space-x-2">
                            <div class="w-3 h-3 bg-green-500 rounded-full"></div>
                            <span>Delivered (${shipments.filter(s => s.status === 'delivered').length})</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <div class="w-3 h-3 bg-orange-500 rounded-full"></div>
                            <span>In Transit (${shipments.filter(s => s.status === 'in_transit').length})</span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <div class="w-3 h-3 bg-red-500 rounded-full"></div>
                            <span>Out for Delivery (${shipments.filter(s => s.status === 'out_for_delivery').length})</span>
                        </div>
                    </div>
                </div>
                
                <!-- Real-time updates indicator -->
                <div class="absolute bottom-4 right-4 flex items-center space-x-2 bg-black bg-opacity-70 text-white px-3 py-1 rounded-full">
                    <div class="w-2 h-2 bg-green-500 rounded-full animate-pulse"></div>
                    <span class="text-xs">LIVE UPDATES</span>
                </div>
            `;
        }

        function drawDeliveryChart() {
            const canvas = document.getElementById('deliveryChart');
            if (!canvas) return;
            
            const ctx = canvas.getContext('2d');
            const width = canvas.width;
            const height = canvas.height;
            
            // Clear canvas
            ctx.clearRect(0, 0, width, height);
            
            // Draw background
            ctx.fillStyle = '#1f2937';
            ctx.fillRect(0, 0, width, height);
            
            // Sample delivery data for the last 7 days
            const deliveryData = [12, 18, 15, 22, 19, 25, 20];
            const days = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];
            const maxDeliveries = Math.max(...deliveryData);
            
            // Draw bars
            const barWidth = width / deliveryData.length - 20;
            const barSpacing = 20;
            
            deliveryData.forEach((deliveries, index) => {
                const barHeight = (deliveries / maxDeliveries) * (height - 60);
                const x = index * (barWidth + barSpacing) + 10;
                const y = height - barHeight - 30;
                
                // Draw bar
                const gradient = ctx.createLinearGradient(0, y, 0, y + barHeight);
                gradient.addColorStop(0, '#10b981');
                gradient.addColorStop(1, '#059669');
                
                ctx.fillStyle = gradient;
                ctx.fillRect(x, y, barWidth, barHeight);
                
                // Draw value on top
                ctx.fillStyle = '#e5e7eb';
                ctx.font = '12px Inter';
                ctx.textAlign = 'center';
                ctx.fillText(deliveries.toString(), x + barWidth / 2, y - 5);
                
                // Draw day label
                ctx.fillStyle = '#9ca3af';
                ctx.fillText(days[index], x + barWidth / 2, height - 10);
            });
            
            // Draw title
            ctx.fillStyle = '#f3f4f6';
            ctx.font = 'bold 14px Inter';
            ctx.textAlign = 'left';
            ctx.fillText('Daily Deliveries (Last 7 Days)', 10, 20);
        }

        function refreshMap() {
            updateAdminDeliveryMap();
            
            // Show refresh animation
            const button = event.target;
            button.classList.add('animate-spin');
            setTimeout(() => {
                button.classList.remove('animate-spin');
            }, 1000);
            
            logActivity('Delivery Management', 'Refreshed delivery map');
        }

        function addNewShipment() {
            // This would open a modal to add new shipment in a full implementation
            const shipmentId = `HE${Date.now()}US`;
            const newShipment = {
                id: shipmentId,
                orderId: `#${Math.floor(Math.random() * 90000) + 10000}`,
                customerName: 'New Customer',
                customerEmail: 'customer@example.com',
                items: ['New Product'],
                status: 'pending',
                currentLocation: { lat: 40.7128, lng: -74.0060, name: 'Warehouse' },
                destination: { lat: 40.7589, lng: -73.9851, name: 'Customer Address' },
                route: [
                    { lat: 40.7128, lng: -74.0060, name: 'Warehouse', timestamp: null, status: 'pending' }
                ],
                estimatedDelivery: new Date(Date.now() + 3 * 24 * 60 * 60 * 1000).toISOString(),
                carrier: 'HUSTLE Express',
                service: 'Standard Delivery',
                weight: '2.0 lbs',
                createdAt: new Date().toISOString(),
                lastUpdate: new Date().toISOString()
            };
            
            shipments.push(newShipment);
            localStorage.setItem('shipments', JSON.stringify(shipments));
            updateDeliveryTracking();
            
            alert(`New shipment ${shipmentId} created successfully!`);
            logActivity('Delivery Management', `Created new shipment ${shipmentId}`);
        }

        function viewShipmentDetails(shipmentId) {
            const shipment = shipments.find(s => s.id === shipmentId);
            if (!shipment) return;
            
            alert(`📦 Shipment Details\n\nID: ${shipment.id}\nOrder: ${shipment.orderId}\nCustomer: ${shipment.customerName}\nStatus: ${shipment.status}\nCurrent Location: ${shipment.currentLocation.name}\nEstimated Delivery: ${new Date(shipment.estimatedDelivery).toLocaleDateString()}\n\nItems: ${shipment.items.join(', ')}`);
        }

        function updateShipmentStatus(shipmentId) {
            const shipment = shipments.find(s => s.id === shipmentId);
            if (!shipment) return;
            
            const newStatus = prompt(`Update status for ${shipment.id}:\n\nCurrent: ${shipment.status}\n\nEnter new status (pending, picked_up, in_transit, out_for_delivery, delivered, delayed):`, shipment.status);
            
            if (newStatus && ['pending', 'picked_up', 'in_transit', 'out_for_delivery', 'delivered', 'delayed'].includes(newStatus)) {
                shipment.status = newStatus;
                shipment.lastUpdate = new Date().toISOString();
                
                // Update route if status changed
                if (newStatus === 'delivered') {
                    shipment.actualDelivery = new Date().toISOString();
                    const lastStop = shipment.route[shipment.route.length - 1];
                    if (!lastStop.timestamp) {
                        lastStop.timestamp = new Date().toISOString();
                        lastStop.status = 'delivered';
                    }
                }
                
                localStorage.setItem('shipments', JSON.stringify(shipments));
                updateDeliveryTracking();
                
                alert(`Shipment ${shipmentId} status updated to: ${newStatus}`);
                logActivity('Delivery Management', `Updated shipment ${shipmentId} status to ${newStatus}`);
            }
        }

        function resolveAlert(alertId) {
            alert(`Alert ${alertId} has been resolved.`);
            logActivity('Delivery Management', `Resolved delivery alert ${alertId}`);
        }

        function dismissAlert(alertId) {
            alert(`Alert ${alertId} has been dismissed.`);
            logActivity('Delivery Management', `Dismissed delivery alert ${alertId}`);
        }
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'96c880a0678c7408',t:'MTc1NDc1NTYwNC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

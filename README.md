<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tushar Tech Zone</title>

  <script src='//libtl.com/sdk.js' data-zone='8690632' data-sdk='show_8690632'></script>

  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <script src="https://unpkg.com/lucide@latest"></script>

  <style>
    body { font-family: 'Inter', sans-serif; background-color: #121212; color: #ffffff; }
    .dark-bg { background-color: #121212; }
    .card-bg { background-color: #1e1e1e; }
    .border-accent { border-color: #ff8c00; }
    .text-accent { color: #ff8c00; }
    .btn, .btn-accent, .btn-outline-accent { transition: all 0.2s ease-in-out; transform: scale(1); }
    .btn:active, .btn-accent:active, .btn-outline-accent:active { transform: scale(0.95); }
    .btn-accent { background-color: #ff8c00; color: #121212; font-weight: bold; }
    .btn-accent:hover { background-color: #e67e00; }
    .btn-outline-accent { border: 1px solid #ff8c00; color: #ff8c00; }
    .btn-outline-accent:hover { background-color: #ff8c00; color: #121212; }
    .input-field { background-color: #2c2c2c; border: 1px solid #444; }
    .main-page { display: none; }
    .main-page.active { display: flex; animation: fadeIn 0.5s ease-in-out; }
    .sub-page { display: none; }
    .sub-page.active { display: block; animation: fadeIn 0.3s ease-in-out; }
    .bottom-nav a.active { color: #ff8c00; }
    .notification-dot {
      position: absolute; top: -2px; right: -2px; width: 10px; height: 10px;
      background-color: #ef4444; border-radius: 50%; border: 2px solid #121212; display: none;
    }
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
  </style>
</head>

<body class="max-w-md mx-auto">

  <div id="loader" class="hidden fixed inset-0 dark-bg bg-opacity-75 flex items-center justify-center z-50">
    <div class="animate-spin rounded-full h-16 w-16 border-t-2 border-b-2 border-accent"></div>
  </div>

  <div id="timer-modal" class="hidden fixed inset-0 bg-black bg-opacity-90 flex items-center justify-center z-50 p-6">
    <div class="bg-gray-800 rounded-lg p-8 w-full max-w-sm text-center">
      <h3 class="text-xl font-bold mb-4 text-accent">Please Wait</h3>
      <div class="text-4xl font-bold mb-4" id="countdown-display">0</div>
      <p class="text-gray-400 text-sm">Do not close the app or the window.</p>
    </div>
  </div>

  <div id="auth-section" class="min-h-screen p-6 flex-col justify-center main-page">
    <h1 class="text-3xl font-bold text-center mb-2 text-accent">Tushar Tech Zone</h1>
    <p class="text-center text-gray-400 mb-8">Login or Signup to continue</p>

    <div id="auth-container">
      <div id="login-view">
        <input id="login-email" type="email" placeholder="Email" class="w-full p-3 rounded-lg input-field mb-4">
        <input id="login-password" type="password" placeholder="Password" class="w-full p-3 rounded-lg input-field mb-4">
        <button id="login-btn" class="w-full p-3 rounded-lg btn-accent mb-4">Login</button>
        <p class="text-center text-gray-400">Don't have an account?
          <a href="#" id="show-signup" class="font-semibold text-accent">Sign Up</a>
        </p>
      </div>

      <div id="signup-view" class="hidden">
        <input id="signup-name" type="text" placeholder="Full Name" class="w-full p-3 rounded-lg input-field mb-4">
        <input id="signup-email" type="email" placeholder="Email" class="w-full p-3 rounded-lg input-field mb-4">
        <input id="signup-password" type="password" placeholder="Password" class="w-full p-3 rounded-lg input-field mb-4">
        <button id="signup-btn" class="w-full p-3 rounded-lg btn-accent mb-4">Sign Up</button>
        <p class="text-center text-gray-400">Already have an account?
          <a href="#" id="show-login" class="font-semibold text-accent">Login</a>
        </p>
      </div>
    </div>
  </div>

  <div id="app-container" class="min-h-screen flex-col main-page">
    <header class="flex items-center justify-between p-4 sticky top-0 bg-opacity-80 backdrop-blur-md z-10 dark-bg">
      <h1 class="text-xl font-bold">Tushar Tech Zone</h1>
      <div class="flex items-center space-x-4">
        <div id="notification-bell" class="relative cursor-pointer">
          <i data-lucide="bell" class="w-6 h-6"></i>
          <div id="notification-dot" class="notification-dot"></div>
        </div>
        <i data-lucide="user" class="w-6 h-6 cursor-pointer" onclick="navigateTo('profile-page')"></i>
      </div>
    </header>

    <main class="flex-grow">

      <div id="home-page" class="p-4 space-y-6 sub-page">
        <div class="card-bg p-4 rounded-lg flex items-center justify-between">
          <div>
            <p class="text-gray-400 text-sm">Your Balance</p>
            <p class="text-3xl font-bold"><span id="coin-balance">0</span> Coins</p>
          </div>
          <button id="home-withdraw-btn" class="bg-white text-black font-semibold px-6 py-2 rounded-lg">Withdraw</button>
        </div>

        <section>
          <div class="flex justify-between items-center">
            <div>
              <h2 class="text-lg font-semibold">Daily Tasks</h2>
              <p class="text-sm text-gray-400 mb-4">Complete tasks to get rewards.</p>
            </div>
            <p class="text-sm text-gray-400">Ads Left: <span id="ads-left-count">...</span></p>
          </div>

          <div class="space-y-3">
            
            <div class="bg-orange-500 p-3 rounded-lg flex items-center justify-between text-black">
              <div class="flex items-center space-x-3">
                <span class="text-3xl">ðŸ¤©</span>
                <div>
                  <h3 class="font-bold">Watch Short Ad</h3>
                  <p class="text-xs font-medium">Instant Reward</p>
                </div>
              </div>
              <button class="bg-white text-orange-500 font-bold px-6 py-2 rounded-lg text-sm btn" onclick="claimReward('interstitial')">Claim</button>
            </div>

            <div class="card-bg p-3 rounded-lg flex items-center justify-between">
              <div class="flex items-center space-x-3">
                <span class="text-3xl">â³</span>
                <div>
                  <h3 class="font-semibold">Daily Task Click</h3>
                  <p class="text-xs text-gray-400">Wait 30 Seconds</p>
                </div>
              </div>
              <button class="bg-white text-black font-bold px-6 py-2 rounded-lg text-sm btn" onclick="claimReward('dailyClick')">Start</button>
            </div>

            <div class="card-bg p-3 rounded-lg flex items-center justify-between">
              <div class="flex items-center space-x-3">
                <span class="text-3xl">ðŸŒ</span>
                <div>
                  <h3 class="font-semibold">Website Visit Income</h3>
                  <p class="text-xs text-gray-400">Wait 20 Seconds</p>
                </div>
              </div>
              <button class="bg-blue-600 text-white font-bold px-6 py-2 rounded-lg text-sm btn" onclick="claimReward('websiteVisit')">Visit</button>
            </div>

            <div class="card-bg p-3 rounded-lg flex items-center justify-between">
              <div class="flex items-center space-x-3">
                <span class="text-3xl">ðŸŒ</span>
                <div>
                  <h3 class="font-semibold">Website Visit Income</h3>
                  <p class="text-xs text-gray-400">Wait 20 Seconds</p>
                </div>
              </div>
              <button class="bg-blue-600 text-white font-bold px-6 py-2 rounded-lg text-sm btn" onclick="claimReward('websiteVisit')">Visit</button>
            </div>

            <div class="card-bg p-3 rounded-lg flex items-center justify-between">
              <div class="flex items-center space-x-3">
                <span class="text-3xl">ðŸŽ®</span>
                <div>
                  <h3 class="font-semibold">Play Mini App</h3>
                  <p class="text-xs text-gray-400">Get a big reward!</p>
                </div>
              </div>
              <button class="bg-green-600 text-white font-bold px-6 py-2 rounded-lg text-sm btn" onclick="claimReward('miniApp')">Play</button>
            </div>
          </div>
        </section>
      </div>

      <div id="wallet-page" class="p-4 space-y-6 sub-page">
        <h2 class="text-xl font-bold text-center">My Wallet</h2>

        <div class="card-bg p-4 rounded-lg">
          <h3 class="font-semibold mb-3">Withdraw Earnings</h3>
          <p class="text-sm text-gray-400 mb-1">
            Current Balance:
            <span class="font-bold text-accent"><span id="wallet-coin-balance">0</span> Coins</span>
          </p>
          <p class="text-sm text-gray-400 mb-2">Minimum Withdrawal: <span id="min-withdrawal-info">...</span> Coins</p>
          <p class="text-sm text-gray-400 mb-4 font-semibold" id="coin-value-info">...</p>

          <input id="withdraw-amount" type="number" placeholder="Enter coin amount" class="w-full p-3 rounded-lg input-field mb-3">
          <select id="withdraw-method" class="w-full p-3 rounded-lg input-field mb-3"></select>
          <div id="payment-details-container"></div>

          <button id="withdraw-btn" class="w-full p-3 rounded-lg btn-accent mt-3">Request Withdrawal</button>
        </div>

        <div>
          <h3 class="text-lg font-semibold mb-3">Withdrawal History</h3>
          <div id="withdrawal-history-list" class="space-y-3"></div>
        </div>
      </div>

      <div id="refer-page" class="p-4 space-y-6 sub-page">
        <h2 class="text-xl font-bold text-center">Refer & Earn</h2>

        <div class="card-bg p-6 rounded-lg text-center">
          <p class="text-gray-400 mb-2">Your Referral Code</p>
          <div class="bg-gray-800 p-3 rounded-lg flex items-center justify-center mb-4">
            <span id="referral-code" class="text-2xl font-bold tracking-widest">LOADING...</span>
            <button id="copy-code-btn" class="ml-4"><i data-lucide="copy" class="w-6 h-6 text-gray-400"></i></button>
          </div>
          <p class="text-sm text-gray-300">Share the code with your friends.</p>
        </div>

        <button id="share-btn" class="w-full p-3 rounded-lg btn-accent">Share Your Code</button>

        <div class="card-bg p-4 rounded-lg mt-6">
          <h3 class="font-semibold mb-3 text-center">Have a Referral Code?</h3>
          <input id="enter-referral-code" type="text" placeholder="Enter code here" class="w-full p-3 rounded-lg input-field mb-3">
          <button id="apply-referral-btn" class="w-full p-3 rounded-lg btn-outline-accent">Apply Code</button>
        </div>
      </div>

      <div id="profile-page" class="p-4 space-y-6 sub-page">
        <h2 class="text-xl font-bold text-center mb-4">Profile</h2>
        <div class="flex flex-col items-center">
          <img src="https://placehold.co/100x100/1e1e1e/ff8c00?text=U" class="rounded-full mb-2">
          <h2 id="profile-name" class="text-xl font-bold">User Name</h2>
          <p id="profile-email" class="text-gray-400">user@email.com</p>
        </div>
        <button id="logout-btn" class="w-full mt-6 p-3 rounded-lg bg-red-600 text-white font-bold">Logout</button>
      </div>

      <div id="notifications-page" class="p-4 space-y-4 sub-page">
        <h2 class="text-xl font-bold text-center">Notifications</h2>
        <div id="notifications-list" class="space-y-3"></div>
      </div>

    </main>

    <nav class="bottom-nav sticky bottom-0 grid grid-cols-4 items-center text-center py-2 card-bg">
      <a href="#" class="nav-link" data-page="home-page"><i data-lucide="home" class="mx-auto w-6 h-6"></i><span class="text-xs">Home</span></a>
      <a href="#" class="nav-link" data-page="wallet-page"><i data-lucide="wallet" class="mx-auto w-6 h-6"></i><span class="text-xs">Wallet</span></a>
      <a href="#" class="nav-link" data-page="refer-page"><i data-lucide="users" class="mx-auto w-6 h-6"></i><span class="text-xs">Refer & Earn</span></a>
      <a href="#" class="nav-link" data-page="profile-page"><i data-lucide="user" class="mx-auto w-6 h-6"></i><span class="text-xs">Profile</span></a>
    </nav>
  </div>

  <div id="custom-alert" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4">
    <div class="bg-gray-800 rounded-lg p-6 w-full max-w-sm text-center">
      <p id="alert-message" class="mb-4"></p>
      <button id="alert-ok-btn" class="btn-accent px-6 py-2 rounded-lg">OK</button>
    </div>
  </div>

  <script type="module">
    // FIREBASE CONFIG
    const firebaseConfig = {
      apiKey: "AIzaSyAb_jZR8sTHH7JzyCCL3Usxdxx5PpRxy5M",
      authDomain: "tm-earning-bot.firebaseapp.com",
      databaseURL: "https://tm-earning-bot-default-rtdb.firebaseio.com",
      projectId: "tm-earning-bot",
      storageBucket: "tm-earning-bot.firebasestorage.app",
      messagingSenderId: "235329914382",
      appId: "1:235329914382:web:b4a51918816a573f079e5f",
      measurementId: "G-7CJJE73TH5"
    };

    import { initializeApp } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-app.js";
    import {
      getAuth, onAuthStateChanged,
      createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut,
      updateProfile
    } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-auth.js";
    import {
      getFirestore, doc, setDoc, getDoc, updateDoc,
      collection, addDoc, serverTimestamp,
      query, where, getDocs, orderBy, limit
    } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore.js";

    const app = initializeApp(firebaseConfig);
    const auth = getAuth(app);
    const db = getFirestore(app);

    let currentUser = null;
    let userData = null;
    let appConfig = {};

    const loader = document.getElementById('loader');
    const coinBalanceEl = document.getElementById('coin-balance');
    const walletCoinBalanceEl = document.getElementById('wallet-coin-balance');
    const profileNameEl = document.getElementById('profile-name');
    const profileEmailEl = document.getElementById('profile-email');
    const referralCodeEl = document.getElementById('referral-code');
    const minWithdrawalInfoEl = document.getElementById('min-withdrawal-info');
    const coinValueInfoEl = document.getElementById('coin-value-info');
    const withdrawMethodSelect = document.getElementById('withdraw-method');
    const notificationDot = document.getElementById('notification-dot');
    const adsLeftCountEl = document.getElementById('ads-left-count');
    const paymentDetailsContainer = document.getElementById('payment-details-container');
    const timerModal = document.getElementById('timer-modal');
    const countdownDisplay = document.getElementById('countdown-display');

    window.onload = () => {
      lucide.createIcons();
      setupEventListeners();
      showMainPage('auth-section');
      loader.classList.add('hidden');
      onAuthStateChanged(auth, handleAuthStateChange);
    };

    function showLoader(show) {
      if (show) loader.classList.remove('hidden');
      else loader.classList.add('hidden');
    }

    async function handleAuthStateChange(user) {
      if (user) {
        showLoader(true);
        currentUser = user;
        await fetchUserData();
        if (userData?.isBlocked) {
          showAlert("Your account has been blocked.");
          await signOut(auth);
          showLoader(false);
          return;
        }
        await fetchAppConfig();
        await checkNewNotifications();
        await ensureDailyCounterSync();
        updateUI();
        showMainPage('app-container');
        navigateTo('home-page');
        showLoader(false);
      } else {
        currentUser = null;
        userData = null;
        showMainPage('auth-section');
      }
    }

    async function fetchUserData() {
      if (!currentUser) return;
      const userRef = doc(db, "users", currentUser.uid);
      try {
        const snap = await getDoc(userRef);
        if (snap.exists()) {
          userData = snap.data();
          return;
        }
        const ownReferralCode = Math.random().toString(36).substring(2, 8).toUpperCase();
        const defaultUserData = {
          uid: currentUser.uid,
          name: currentUser.displayName || (currentUser.email ? currentUser.email.split('@')[0] : "User"),
          email: currentUser.email || "",
          balance: 50,
          referralCode: ownReferralCode,
          referredBy: null,
          lastNotificationCheck: serverTimestamp(),
          createdAt: serverTimestamp(),
          dailyAdCount: 0,
          lastAdWatchDate: new Date().toISOString().split('T')[0],
          isBlocked: false
        };
        await setDoc(userRef, defaultUserData, { merge: true });
        userData = { ...defaultUserData, lastNotificationCheck: null };
      } catch (e) {
        console.error("fetchUserData error:", e);
        showAlert("Error loading user data.");
      }
    }

    async function fetchAppConfig() {
      const configRef = doc(db, "config", "main");
      try {
        const snap = await getDoc(configRef);
        appConfig = snap.exists()
          ? snap.data()
          // UPDATED DEFAULT CONFIG: Bkash, Nagad, Rocket
          : {
              minWithdrawal: 5000,
              paymentMethods: ["Bkash", "Nagad", "Rocket"],
              dailyAdLimit: 15, // Increased limit for more tasks
              coinValueCoins: 1000,
              coinValueInr: 10
            };
        
        // Ensure default fallback uses the requested methods if DB is empty
        if (!appConfig.paymentMethods || appConfig.paymentMethods.length === 0) {
           appConfig.paymentMethods = ["Bkash", "Nagad", "Rocket"];
        }

      } catch (e) {
        console.error("fetchAppConfig error:", e);
        appConfig = { minWithdrawal: 5000, paymentMethods: ["Bkash", "Nagad", "Rocket"], dailyAdLimit: 15, coinValueCoins: 1000, coinValueInr: 10 };
      }
    }

    function updateUI() {
      if (!userData) return;

      const balance = userData.balance || 0;
      coinBalanceEl.textContent = balance;
      walletCoinBalanceEl.textContent = balance;

      profileNameEl.textContent = userData.name || "No Name";
      profileEmailEl.textContent = userData.email || "No Email";
      referralCodeEl.textContent = userData.referralCode || "...";
      minWithdrawalInfoEl.textContent = `${appConfig.minWithdrawal || 5000} Coins`;
      coinValueInfoEl.textContent = `${appConfig.coinValueCoins || 1000} Coins = à§³${appConfig.coinValueInr || 10}`;

      withdrawMethodSelect.innerHTML = "";
      (appConfig.paymentMethods || []).forEach((method) => {
        const opt = document.createElement("option");
        opt.value = method;
        opt.textContent = method;
        withdrawMethodSelect.appendChild(opt);
      });

      updateDynamicPaymentFields();
      updateAdsLeftCount();
    }

    function showMainPage(pageId) {
      document.querySelectorAll(".main-page").forEach(p => p.classList.remove("active"));
      document.getElementById(pageId).classList.add("active");
    }

    function navigateTo(pageId) {
      document.querySelectorAll(".sub-page").forEach(p => p.classList.remove("active"));
      document.getElementById(pageId).classList.add("active");
      document.querySelectorAll(".nav-link").forEach(link => {
        link.classList.remove("active", "text-accent");
        if (link.dataset.page === pageId) link.classList.add("active", "text-accent");
      });
    }
    window.navigateTo = navigateTo;

    function setupEventListeners() {
      document.getElementById('show-signup').addEventListener('click', (e) => {
        e.preventDefault();
        document.getElementById('login-view').classList.add('hidden');
        document.getElementById('signup-view').

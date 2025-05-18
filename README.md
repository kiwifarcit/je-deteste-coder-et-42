<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Police Orbitron -->
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&display=swap" rel="stylesheet">
    
    <!-- Style CSS (chargé après Tailwind) -->
    <link href="style.css" rel="stylesheet">

    <title>Trong</title>

    <!-- Configuration Tailwind -->
    <script>
      tailwind.config = {
        theme: {
          extend: {
            fontFamily: {
              gamer: ['Orbitron', 'sans-serif'],
            },
            colors: {
              neon: {
                blue: '#00f0ff',
                pink: '#ff00c3',
                purple: '#a200ff',
              },
            }
          }
        }
      }
    </script>
</head>

<body class="h-screen content-center bg-gradient-to-br from-purple-600 to-blue-500">

    <!-- LOGIN FORM -->
    <div id="login-form" class="flex flex-col p-6 bg-white border border-gray-200 rounded-lg shadow-sm dark:bg-gray-800 dark:border-gray-700 max-w-sm mx-auto mb-5"  style="display:none">
        <h1 class="underline text-white text-4xl text-center" id="form-title">Connexion</h1>

        <form class="max-w-sm mx-auto" id="form">
            <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white" for="username">Username</label>
            <input class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" id="username" name="username" required />

            <label class="block mb-2 text-sm font-medium text-gray-900 dark:text-white" for="password">Password</label>
            <input class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" id="password" name="password" type="password" required />

            <p style="display:none;" class="text-red-600" id="errorAuth"></p>

            <a class="font-medium text-blue-600 hover:underline dark:text-blue-500" id="register-view" href="#">S'inscrire</a>
            <button id="login_btn" class="my-2 w-full text-white bg-gradient-to-br from-green-400 to-blue-600 hover:bg-gradient-to-bl focus:ring-4 focus:outline-none focus:ring-green-200 dark:focus:ring-green-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2" type="submit">Se connecter</button>
        </form>
        
    </div>

    <div id="site" style="display: none;">
        <div id="pong-game">
            <div id="gameContainer">
                <h1 class="mb-50 underline text-white text-7xl text-center cursor-pointer" id="game_title">Trong the Game</h1>
                <!-- SCOREBOARD -->
                <div id="scoreboard" style="font-size: 24px; font-weight: bold; margin-bottom: 10px; display: none;">
                    <span id="player-left">Player 1</span> 
                    <span id="score-left">0</span> - 
                    <span id="score-right">0</span>
                    <span id="player-right">Player 2</span>
                </div>
                <!-- MENU -->
                <div id="pageContent" class="flex w-full justify-between">
                    <!-- Premier UL : 70% -->
                    <ul id="menu" class="block w-[70%] space-y-6 text-gray-500 list-none dark:text-gray-400">
                        <li>
                            <button id="offline" class="w-[90%] hover:w-full transition-all duration-500 ease-in-out cursor-pointer p-12 text-5xl italic font-medium dark:text-black bg-gradient-to-br from-purple-500 to-pink-500 rounded-lg border-4 border-purple-600 flex items-center justify-center text-center">
                                Play local
                            </button>
                        </li>
                        <li>
                            <button id="matchmaking" class="w-[90%] hover:w-full transition-all duration-500 ease-in-out cursor-pointer p-12 text-5xl italic font-medium dark:text-black bg-gradient-to-r from-teal-200 to-lime-200 hover:from-lime-200 hover:to-teal-200 rounded-lg border-4 border-green-800 flex items-center justify-center text-center">
                                Play online
                            </button>
                        </li>
                        <li>
                            <button id="matchmaking" class="w-[90%] hover:w-full transition-all duration-500 ease-in-out cursor-pointer p-12 text-5xl italic font-medium dark:text-black bg-gradient-to-br from-green-400 to-blue-600 hover:bg-gradient-to-bl focus:ring-4 focus:outline-none focus:ring-green-200 dark:focus:ring-green-800 rounded-lg border-4 border-green-800 flex items-center justify-center text-center">
                                Tournament
                            </button>
                        </li>
                        <li>
                            <button id="profile_button" class="w-[90%] hover:w-full transition-all duration-500 ease-in-out cursor-pointer p-12 text-5xl italic font-medium dark:text-black bg-gradient-to-r from-red-200 via-red-300 to-yellow-200 hover:from-yellow-200 hover:to-red-300 rounded-lg border-4 border-red-600 flex items-center justify-center text-center">
                                Profile
                            </button>
                        </li>
                        <li>
                            <button class="w-[90%] hover:w-full transition-all duration-500 ease-in-out cursor-pointer p-12 text-5xl italic font-medium dark:text-black bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-blue-500 hover:to-cyan-500 rounded-lg border-4 border-blue-700 flex items-center justify-center text-center">
                                About
                            </button>
                        </li>
                    </ul>
                    

                           
<div id="player_profile" class="max-w-5xl mx-auto space-y-10 font-gamer">

  <!-- Bloc Profil -->
  <div class="bg-gray-900 border-2 border-neon-purple p-6 rounded-xl shadow-2xl grid grid-cols-1 md:grid-cols-3 gap-6 items-center">
    
    <!-- Avatar -->
    <div class="relative mx-auto md:mx-0 w-28 h-28">
      <img id="profile_picture" class="w-full h-full rounded-full object-cover border-4 border-neon-blue" src="https://via.placeholder.com/100" />
      <img id="camera_icon" src="assets/imgs/hoverPicture.png"
           class="absolute top-1 right-1 w-7 h-7 opacity-0 hover:opacity-100 transition-opacity duration-200 cursor-pointer" />
    </div>

    <!-- Infos utilisateur -->
    <div class="col-span-2 text-center md:text-left">
      <h1 id="profile_username" class="text-3xl font-bold text-neon-blue">Username</h1>
      <p id="profile_creation" class="text-sm text-gray-400 mt-1">Membre depuis le 14 mai 2025</p>
      <div id="friend_div" class="flex justify-center md:justify-start gap-3 mt-4">
        <button id="friend_btn" class="px-4 py-2 bg-neon-blue hover:bg-blue-400 text-black font-bold rounded-lg shadow">Ajouter</button>
        <button id="block_btn" class="px-4 py-2 bg-red-600 hover:bg-red-700 text-white font-bold rounded-lg shadow">🔒 Bloquer</button>
      </div>
    </div>
  </div>

  <!-- Recherche de joueurs -->
  <div id="search_container" class="flex flex-col sm:flex-row items-stretch sm:items-center gap-3">
    <input id="search_player_in" type="text" placeholder="Chercher un joueur..."
           class="flex-1 px-4 py-2 bg-gray-800 border border-neon-purple text-white rounded-lg" />
    <button id="search_player_btn" class="px-4 py-2 bg-neon-pink hover:bg-pink-600 text-black font-bold rounded-lg">🔍</button>
  </div>

  <!-- Statistiques -->
  <div id="histo" class="bg-gray-900 border-2 border-neon-purple p-6 rounded-xl shadow-xl space-y-6">
    <h2 class="text-2xl text-neon-pink font-bold">Statistiques</h2>

    <div class="flex flex-col md:flex-row items-center justify-between gap-6">
      <!-- Graphique -->
      <div class="flex justify-center md:justify-start">
        <svg id="wr_graph" viewBox="0 0 36 36" class="w-24 h-24">
          <path class="stroke-gray-700 fill-none stroke-[3]" stroke-dasharray="100,100"
                d="M18 2.0845a15.9155 15.9155 0 0 1 0 31.831a15.9155 15.9155 0 0 1 0-31.831"/>
          <path id="percent" class="stroke-neon-blue fill-none stroke-[3] stroke-linecap-round" stroke-dasharray="30,100"
                d="M18 2.0845a15.9155 15.9155 0 0 1 0 31.831a15.9155 15.9155 0 0 1 0-31.831"/>
          <text id="wr" x="18" y="14" text-anchor="middle" dy="7"
                class="fill-white text-base font-bold">3/10</text>
        </svg>
      </div>

      <!-- Historique -->
      <ul id="histo_list" class="flex-1 list-disc pl-5 text-sm text-gray-300 space-y-1">
        <li>Match contre Player1 - <span class="text-green-400">victoire</span></li>
        <li>Match contre Player2 - <span class="text-red-400">défaite</span></li>
        <li>Match contre Player3 - <span class="text-green-400">victoire</span></li>
      </ul>
    </div>
  </div>

</div>

                    <!-- Friendlist box -->
                    <div class="w-[20%] overflow-y-auto bg-gray-100 dark:bg-gray-800 rounded-lg p-4 border border-gray-300 dark:border-gray-700 shadow-inner">
                        <div class="flex justify-between items-center mb-4">
                            <h2 class="text-xl font-bold text-gray-800 dark:text-gray-100">Amis connectés</h2>
                        </div>
                        
                        <div id="friendlist" class="w-[20%] h-[80vh] overflow-y-auto bg-gray-100 dark:bg-gray-800 rounded-lg p-4 border border-gray-300 dark:border-gray-700 shadow-inner transform transition-transform duration-300 ease-in-out translate-x-full fixed top-20 right-0 z-40 hidden md:block">
                            <div id="friendsContainer" class="space-y-3">

                            </div>
                        </div>
                    </div>
            </div>
        </div>
            <!-- JEU -->
            <canvas id="pong" width="1490" height="880" style="border: 2px solid #ccc; position: absolute; top: 0; left: 0; margin-right: 10px; z-index: 1; display:none" autofocus></canvas>
        </div>
        <!-- CHAT -->
        <!-- <div id="chat" style="flex: 1; display: none; flex-direction: column; align-items: center; margin-bottom: 20px; padding-left: 10px; border: 2px solid #ccc; overflow: hidden; background-color: black">
            <div id="chatbox" style="height: 100%; padding: 12px; background-color: rgb(99, 123, 145); overflow-y: scroll; width: 100%;"></div>
            <div id="userInput" style="width: 100%; display: flex;">
                <input id="message_input" type="text" placeholder="write message" value="" style="margin: 5px; width: 90%;"/>
                <button id="send_message" style="margin: 5px; width: 10%;">Send</button>
            </div> -->
        <!-- </div> -->
      
      </div>
      
      

    <script src="app.js"></script>
    <script src="pong.js"></script>
    <script src="chat.js"></script>
</body>
</html>

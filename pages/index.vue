<template>
    <div class="bg-no-repeat home h-screen w-screen relative overflow-hidden">
      <NavBar />
        <div class="xl:hidden flex flex-col w-screen mt-6 p-10 justify-center items-center">
          <div class="card w-48 sm:w-96">
              <div class="flex justify-center">
                <svg 
                  class="w-64 h-64 text-white"
                  xmlns="http://www.w3.org/2000/svg" 
                  viewBox="0 0 24 24" 
                  fill="currentColor">
                  <path fillRule="evenodd" d="M2.25 5.25a3 3 0 013-3h13.5a3 3 0 013 3V15a3 3 0 01-3 3h-3v.257c0 .597.237 1.17.659 1.591l.621.622a.75.75 0 01-.53 1.28h-9a.75.75 0 01-.53-1.28l.621-.622a2.25 2.25 0 00.659-1.59V18h-3a3 3 0 01-3-3V5.25zm1.5 0v7.5a1.5 1.5 0 001.5 1.5h13.5a1.5 1.5 0 001.5-1.5v-7.5a1.5 1.5 0 00-1.5-1.5H5.25a1.5 1.5 0 00-1.5 1.5z" clipRule="evenodd" />
                </svg>
              </div>
            <p class="text-white text-2xl mx-auto text-center">Try Bigger Screen 👀</p>
          </div>
        </div>

      <div class="hidden xl:grid grid-cols-2">
        <div class="p-32 pr-10">
          <div class="card">
            <p class="text-5xl text-white">Play the Demo</p>
          </div>
        </div>
        <div class="p-32 pl-10">
          <div class="card">
            <p class="text-5xl text-white">Start the Game 🚀🚀</p>
            <button onclick="connect();"> Connect Wallet </button>
          </div>
        </div>
      </div>
  </div>

</template>

<script>
async function connect() {
  if (window.ethereum) {
     await window.ethereum.request({ method: "eth_requestAccounts" });
     window.web3 = new Web3(window.ethereum);
     const account = web3.eth.accounts;
     //Get the current MetaMask selected/active wallet
     const walletAddress = account.givenProvider.selectedAddress;
     console.log(`Wallet: ${walletAddress}`);
  
  } else {
   console.log("No wallet");
  }
}
export default {
  name: 'IndexPage',
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
  .logo {
    font-family: 'Poppins', sans-serif;
  }
  .home {
    background-image: url(../assets/images/pexels-billel-moula-540518.jpg);
    background-position: center;
    background-size: cover;
  }

  .card {
    height: auto;
    padding: 2rem;
    border-radius: 1rem;
    background: rgba(13, 12, 12, 0.7);
    -webkit-backdrop-filter: blur(5px);
    backdrop-filter: blur(10px);
  }
</style>

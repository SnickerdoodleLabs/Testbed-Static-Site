[![Snickerdoodle Protocol](/snickerdoodle_horizontal_notab.png)](https://snickerdoodle.com)

# Testbed for Static Site Web Integration Package

This is a simple static html page for testing [Snickerdoodle](https://snickerdoodle.com) web-native analytics package. Its meant to 
serve as an example of how to add Snickerdoodle analytics to an existing static html page.

## 1. Add the `snickerdoodle.js` Script to Your Header

Adding [`snickerdoodle.js`](/index.html#L58) to the header of your index.html page will add all wallet connection, airdrop, and analytics 
capabilities supported by Snickerdoodle to your site. 

```
<script src="https://webpackage.snickerdoodle.com/snickerdoodle.js"></script>
```

## 2. Configure Web3 API Keys

Snickerdoodle's analytics package comes with default web3 data provider API keys. However, if you have a large number of user's we strongly 
recommend adding your own web3 API keys to prevent throttling and poor data pipeline performance. 

In your html header (or other appropriate place) call [`snickerdoodle.integrateSnickerdoodle()`](/index.html#L77) with your optional web3 API keys:

```
snickerdoodle.integrateSnickerdoodle({
             primaryInfuraKey: $INFURA_KEY$,
             ankrApiKey: $ANKR_KEY,
             covalentApiKey: $COVALENT_KEY,
             poapApiKey: $POAP_KEY,
             // If you'd like your site to use WalletConnect, provide a ProjectID provisioned
             // from https://cloud.walletconnect.com so use's can connect their mobile wallets
             // NOTE: Snickerdoodle does not provide a default WalletConnect projectID, you must
             // your own to enable its functionality. 
             walletConnect: { 
              projectId: $WALLET_CONNECT_PROJECT_ID,
              metadata_name: "Webthree.Love",
              metadata_description: "Static site integration testbed.",
              metadata_url: "https://www.webthree.love",
             },
           },
         );
```

If you choose to rely on the default API keys for your site, you're code should simply look like this:

```
snickerdoodle.integrationSnickerdoodle({});
```

## 3. Add a TXT Record to Your Site's DNS Settings

You must add a single TXT Record to your site's DNS records so that the analytics package will trigger the user opt-in popup message
when a user connects their wallet to your site. See our [official documentation](https://marketing-docs.snickerdoodle.com/integration-instructions/react-apps#3.-add-a-txt-record-to-your-react-apps-domain) for more information. 

---
description: >-
  If you want to participate in the testing of the Gyro Proto stablecoin, this
  short guide is for you!
---

# Walk-through

## How to use Gyro Proto

To be able to mint p-GYD, proto-GYD dollars, you first need to hold one or more of the tokens that make up the reserve.

Four tokens make up the reserve for Gyro Proto:

<figure><img src="https://lh3.googleusercontent.com/6OhZFTQnDbrK3FVsPktXYYbukkZ1rc03rB_dZo3JiLjOundJCp8gfKKi-PLd7bHSPpYURon3VWpYL16htOIH37K4dZslaTYoxVTo-i9jQa6SIjJYDERRsC1wP2VI-HuRpaDvSHl2oUp9TkP4QjNJ9Liq6PRJnMDcgC6CWbjH0tNj-gj_Zaa8w3tk77zZbw" alt=""><figcaption></figcaption></figure>

3CLP-BUSD-USDC-USDT is, for example, the name of the LP token corresponding to the reserve’s 3CLP pool that contains BUSD and USDC and USDT.

## How do I get LP tokens?

Go to the Gyroscope pool page, [<mark style="color:red;">here</mark>](http://link.gyro.finance)<mark style="color:red;">.</mark> Then, select the LP pool that you want to join and press ‘Join’ on the right side of the page.&#x20;

<figure><img src="https://lh5.googleusercontent.com/Np0c3KpAJc_g3rG3qmXyDLLVnn2TVYzdvjo02Rooi2USk7vuECLkIrS1409bkSP6WNsnZ-jMZOU-dLNcsRcZGLJTr0Rpzme24RHUMNJEGVT_Mc-jzRt1__7YVNfq7b1D86wN8132mv22pDEYfVu_STNp2Xnfmb9e_rpulGaLaoknKaxaW8mOJSVZrrYn6w" alt=""><figcaption></figcaption></figure>

At the moment, to join any of the CLP pools, you need some amount of all of the tokens in the pool. The precise amount will depend on the state of the pool when trying to join. If you don’t have enough of one of the assets, you will see a warning ‘Exceeds Asset Balance’. \


<figure><img src="https://lh4.googleusercontent.com/PsVHP1wM1LPfxgMV5f1bpFS99thspPP-v3MVAZphnTmKsiV8U6qQstkFtiuy7sVrQqEQkaoZRI4k5G2cs9_7p2zozenHF05pgW-l0nJfrv72BAKte9r8PjCX1o3CjkHdLKzzNxX88MorVkDDsIya92_a1WV4Skm4h0jJZQ7WhWjtFBsput7-7plmA8iDLQ" alt=""><figcaption></figcaption></figure>

To acquire more of the asset where the balance is low, you can swap tokens on [Balancer](https://app.balancer.fi/#/polygon/trade), Uniswap, or elsewhere. Once you have enough of each asset, you should see no warning and be able to join the pool.

<figure><img src="https://lh5.googleusercontent.com/2i-1JTeEPixehvHyqRzLIg8oD11grDjME9m_wOnpTgSr9IJfCmbud25Kzjb5DTs6Sin1bUWlEz5QKTR0eGkMNaVoV_HA79KkdNlw9oIk0cPsR87OyM9x7wb1Szmgh7ybOOLrfUNjk2ZNXzPiqOJtJ1QMZIMrQIEz38TcykrC9VBLDpAzfIuxqq7DAUcCkA" alt=""><figcaption></figcaption></figure>

You now own 3CLP-BUSD-USDC-USDT LP tokens.&#x20;

## Minting p-GYD

Now that you have LP tokens, return to the DSM page and connect your wallet.

You can now choose these tokens and add them to your input basket for minting. You can mint with one or more tokens at a time, provided the minting operation keeps the reserves balanced. If the operation would unbalance the reserve, a warning will appear.&#x20;

To make things simpler, we've added a toggle for 'Balanced Mint' - toggling this will ensure that your mint operation would keep the reserve in balance.

We've also added a button 'Select maximum balanced mint' for convenience - this will allow a user to mint the largest balanced mint possible.&#x20;

<figure><img src="../.gitbook/assets/minting.png" alt=""><figcaption></figcaption></figure>



You can also specify the maximum amount of slippage you are prepared to face, and press ‘Mint’.&#x20;

<figure><img src="../.gitbook/assets/mintsuccess.png" alt=""><figcaption></figcaption></figure>

If the transaction succeeds, you should be the proud owner of some p-GYD units of stablecoin!

\
Redeeming p-GYD
---------------

Select the 'Redeem' tab and then specify how many units of p-GYD you want to redeem. Optionally  you can select 'Max' which will redeem all the p-GYD possible in your wallet.&#x20;

<figure><img src="../.gitbook/assets/redemption.png" alt=""><figcaption></figcaption></figure>

Selecting 'Balanced Redemption' will result in a screen such as the following that shows the tokens you will get out of redemption operation:

<figure><img src="../.gitbook/assets/balancedredemption.png" alt=""><figcaption></figcaption></figure>

The balanced redemption reflects the ideal reserve weights. However, provided the reserve will be kept in balance, it is possible to perform a redemption with custom weights.&#x20;

Upon pressing 'Redeem p-GYD' you should see the following screen if the redemption was successful.

<figure><img src="../.gitbook/assets/redemptionsuccess.png" alt=""><figcaption></figcaption></figure>

Congratulations, you've just minted and redeemed some p-GYD!

## How to make p-GYD appear in MetaMask

To make p-GYD appear in MetaMask, you have to import the token address of p-GYD.&#x20;

In the Assets list on MetaMask, import the token using ‘Import tokens’ at the bottom of the list of your assets, and copy and paste the following address into the ‘Token contract address’ field: 0x37b8E1152fB90A867F3dccA6e8d537681B04705E\

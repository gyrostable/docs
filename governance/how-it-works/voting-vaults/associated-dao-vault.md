---
cover: ../../../.gitbook/assets/Associated DAO vault cover.png
coverY: 150.60921248142645
---

# Associated DAO Vault

The composability of DeFi means that sometimes actions in one protocol directly or indirectly affect another protocol. Therefore it makes sense to give such protocols a voice in the governance process.&#x20;

In the Gyroscope governance system, the Associated DAO vault allows governance to assign voting power to another DAO. This is done by calling `FriendlyDAOVault.updateDAOAndTotalWeight`.

Each DAO that is a member of the vault has a share of the total voting power of the vault. The governance system can decide whether to add or remove DAOs from this vault.&#x20;

## Which DAOs are involved?

The DAOs of [Balancer](https://balancer.fi/), [Aura](https://aura.finance/), and [BeethovenX](https://beets.fi/) will constitute the initial members of the Associated DAO vault.

# Governance

## Introduction

Flare governance gives everyone in the ecosystem the opportunity to collaborate on decision-making on the [Flare and Songbird](network-configs.md) networks, making governance an important element of decentralization.

This process enables the Flare Foundation and Flare and Songbird community members to:

* Propose policy changes.
* Vote on them.
* Execute them if accepted.

The following sections detail the different kinds of proposals Flare allows and the process for each of them.

If you are already familiar with Flare's governance and just need to know how to cast your vote through the Flare Portal, check the [Voting User Guide](../user/governance/voting.md).

## Flare's Governance

Excluding the [testnets](glossary.md#test_network) Coston and Coston2, Flare currently has two networks: Flare and Songbird.
Moreover, two kinds of proposals are planned, depending on who initiates them: those proposed by the community and those proposed by the Flare Foundation.

This situation leads to four types of proposals, of which only one is currently supported and detailed next.

### Songbird Test Proposals (STPs)

Songbird Test Proposals are initiated by the Flare Foundation and are aimed at improving the Songbird network.
Community-initiated proposals or those aimed at the Flare network will be supported in the future.

To increase the swiftness at which new proposals can be tested on Songbird, STPs are accepted by default, meaning that they are rejected only if enough votes are cast against them.
Conversely, to increase its stability, future proposals affecting the Flare network will be rejected by default, meaning that they will be accepted only if enough votes are cast in their favor. See [Voting Outcome](#voting-outcome) below for more details.

#### Who Votes

Anyone who holds `$SGB` can vote on STPs.
However, the tokens must be wrapped into `$WSGB` before the proposal is submitted to be able to vote with them.

Once wrapped, every `$WSGB` grants one vote.

!!! important
    Available votes depend on the amount of wrapped tokens (`$WSGB`) held, not the native `$SGB` tokens.
    Therefore, **remember to wrap your tokens**.

!!! important
    When wrapping, **remember to keep some amount of native `$SGB` to pay for transaction fees**.

The Flare Foundation will announce proposals in advance, so that users can read them and wrap their tokens if they have to.

??? info "Vote Transfer"

    Votes can be transferred to another account while the `$WSGB` tokens remain in the user's possession.
    This is useful, for example, if a user has `$WSGB` in multiple self-custody wallets, since voting can then be simplified by transferring all the votes to a single wallet and voting from there.
    {#vote-transfer}

    Votes can only be transferred to one address, but it can receive votes from multiple addresses.
    Received votes cannot be transferred again to a third address.

    **Once activated, vote transfers always send 100% of an account's votes to the selected address and remain active until they are canceled.**

    As an example, if you have 100 `$WSGB` before a proposal and you activate the transfer, you will transfer 100 votes.
    If you later add 100 more `$WSGB`, for the next proposal you will automatically transfer 200 votes, since the transfer remains active until you cancel it.

    The following is a more complex example, showing the changes produced by vote transfers, and token wrapping and unwrapping:

    <figure markdown>
      ![Changes in number of votes](gov-changes-in-number-of-votes.png){ loading=lazy .allow-zoom }
      <figcaption>Changes in the number of votes.</figcaption>
    </figure>

    !!! note
        Transferring votes has no connection with FTSO delegation:
        `$WSGB` tokens can be delegated to an [FTSO data provider](glossary.md#data_provider) and at the same time the votes they grant can be transferred to a different address.

#### The Vote Count Block

Since the amount of `$WSGB` an account holds varies over time, a snapshot of all accounts is taken before each voting period starts.
The amount of `$WSGB` held by an account at the snapshot then dictates the number of votes available later.

The block at which the snapshot is taken is called the **vote count block**.

To encourage users to use their tokens and keep them in the network, instead of just acquiring them for voting and then disposing of them, the vote count block is randomly selected.
The next section details when this happens.

#### Voting Process

<figure markdown>
  ![STP voting process](gov-stp-governance-process.png){ loading=lazy .allow-zoom }
  <figcaption>STP voting process.</figcaption>
</figure>

* **Announcement**: The Flare Foundation publishes the STP online and announces it through social media channels (linked on the footer of this page) and [the Flare website](https://flare.network).

* **Notice period**: Once the proposal is published, the Flare Foundation allows a notice period before voting can start, typically lasting one week.
    During this time the proposal can be discussed, clarified, commented on, and even cancelled if serious issues are found with it.

    For security reasons only, the Foundation may reduce the timeframe of this period.

* **Block selection period**: The [vote count block](#the-vote-count-block) is selected at a random time during this period.
    The duration of this period is also random.

    !!! warning
        If you need to wrap tokens, do so before this period starts since tokens wrapped after the selected vote count block will not result in additional votes.

* **Voting period**: The proposal is submitted to the [Flare Portal](https://portal.flare.network) and it is immediately available for voting.
    Voting concludes after a week, and final results are presented on the portal.

#### Voting Outcome

A vote must satisfy two conditions to pass.
Because voting on STPs is rejection-based, both conditions must hold true for a proposal to be rejected.

* **Threshold condition**: A minimum quorum must be reached, meaning that enough votes must be cast.
    For STPs this quorum is at least 75% of all `$SGB` tokens in circulation (excluding the Flare Foundation's tokens) at the [vote count block](#the-vote-count-block).

    Note that the quorum is specified as a fraction of the circulating native `$SGB` tokens instead of the wrapped tokens `$WSGB` used for voting.
    This measure tries, again, to encourage users to wrap their tokens and use them in the network.

* **Majority condition**: More than 50% of the votes cast, must be against the proposal.

Therefore, an STP will be accepted if the quorum threshold is not reached or if less than half of the cast votes are against it.

#### Execution

Once a proposal is accepted, Flare's governance contracts allow for its automatic execution via a contract call.

However, STPs might require changes that are not implementable through a smart contract and therefore automatic execution is disabled for them.
STPs are manually executed by the Flare Foundation.

### Solana Extensions

Solana extension


A lot has changed in the SPL 2022 standard and one thing that has been introduced to the SPL token are extensions. In this post we will do a quick walkthrough on what they are, why they are needed and the one available.

What are Extensions ?

As the name suggests they are a way to provide further capacity to an SPL token, more precisely a mint. One can during the creation of the mint or even after depending on the extension unable certain features on this one.
We have for example the extension “TransferFee” that will on each transfer in addition to the transferred amount also charge a fee to the user that will then be held by the extension. The owner of the mint will later on be able to harvest it.  The mint still works as any other but once this extension is unable, the mint will have this added behavior.

There are a few extensions right now but I suspect they will start growing more as people see the power of these features and as the Solana ecosystem grows and thus requires more and more use cases.
Here is the list of extension as of writing this post :

<pre><code>
pub enum ExtensionType {
/// Used as padding if the account size would otherwise be 355, same as a multisig
Uninitialized,
/// Includes transfer fee rate info and accompanying authorities to withdraw and set the fee
TransferFeeConfig,
/// Includes withheld transfer fees
TransferFeeAmount,
/// Includes an optional mint close authority
MintCloseAuthority,
/// Auditor configuration for confidential transfers
ConfidentialTransferMint,
/// State for confidential transfers
ConfidentialTransferAccount,
/// Specifies the default Account::state for new Accounts
DefaultAccountState,
/// Indicates that the Account owner authority cannot be changed
ImmutableOwner,
/// Require inbound transfers to have memo
MemoTransfer,
}
</code></pre>

Further will probably be added an the up to date list can be found here : https://github.com/solana-labs/solana-program-library/blob/master/token/program-2022/src/extension/mod.rs#L583

Anyone can create extensions, not so long ago Vitalik wrote a blog post about soul bound NFT https://vitalik.ca/general/2022/01/26/soulbound.html and someone created an implementation of it : https://github.com/solana-labs/solana-program-library/pull/2912

Conclusion

Extensions seems like a good added feature to the omnipresent SPL token program. However, the fact that added features are (for a good reason) gated by the Solana team will greatly limit the range of what can be done.
We thus won't see any crazy token experiment like we saw on Ethereum. 
1. Nikita had engineered the front-end flow to only initialize the v3 profile for users who are bucketed into the experiment. We pointed out to him yesterday that the intent was to move all users to v3 flow. It sounds like a small LOE. Attached is the process flow that you and Andy had put together back in the day and which we have reviewed a few time since.
	1. I thought about what happens with users who are on native? If we are sending everyone through the v3 flow, does this impact users who are using iOS and Android apps? Back when you guys designed the flow, did you talk about native users?
		1. yes, we'll run some tests between the two to see the experiences, but the pure Native only customers shouldn't be affected. 
	2. Would we initialize the v3 profile for native users too even though they are technically not eligible to be bucketed into the experiment?
	3. What happens with users who platform-switch - e.g. start on web and then switch to native at SD step or later, and vice-versa? I asked Vanitha to test some of these cases, but since we have not done the cutover to v3 yet I am not sure that we can properly test this either.
	4. Overall comment for native is that we should figure out a way to run the DDV experiment without asking that team to do any work, if at all possible. Otherwise, we won't be able to launch anything anytime soon. If that means going back and initializing profiles only for users who are bucketed into the experiment, we should consider that. I have no grief with that.
2. One thing we omitted in our design was to update the post-profile (quote, disclaimers and bind/payment) calls to Root to include the v3 quote as the externalId. We now have a bug ticket open for this as well. It's not a major LOE but will take a day or two with hopefully two engs running side-by-side.

1. Again, would this impact users on native, esp. users who platform-switch?


Mobile/Web client switching:

1.  Scenarios
		1. Mobile customer starts on web and moves to native and stays on native.  The web experience will have created a v3 quote.  The Native app makes calls through proxy, and since a v3 quote exists this customer will continue to see the v3 quote from the web.
		2. Mobile customer starts on web and moves to native and moves back to web.  Same as above except if the customer added drivers or vehicles on native then those additions won't show back up on the v3 snapshot and therefore the quote on web.
		3. Mobile customer starts on native and stays on native.  Native app makes calls through proxy, and since no v3 quote exists this customer will continue through the v2 flows as is today.
		4. Mobile customer starts on native and moves to web.  The web app then calls and created a v3 quote for the customer.  The buckets, and then could show prefill or move to the quote screen.  Here the quote will be different.
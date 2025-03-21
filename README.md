# CA--pi
this is capi app
// frontend/src/shop/index.ts

const signIn = async () => {
  const scopes = ["username", "payments"];
  const authResponse = await window.Pi.authenticate(scopes, onIncompletePaymentFound);

  /* pass obtained data to backend */
  await signInUser(authResponse);

  /* use the obtained data however you want */
  setUser(authResponse.user);
};

const signInUser = (authResult: any) => {
  axiosClient.post("/signin", { authResult }, config);

  return setShowModal(false);
};

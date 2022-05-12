<script>
  import { Link, useNavigate } from "svelte-navigator";
  import axios from "axios";

  // login action
  let emailAddress = "";
  let password = "";
  const navigate = useNavigate();

  function handleSubmit() {
    const config = {
      headers: { "Access-Control-Allow-Origin": "*" },
    };
    axios
      .post('/user/login/', { emailAddress, password }, config)
      .then((res) => {
        console.log(res);
        localStorage.setItem("userInfo", JSON.stringify(res.data));
        setTimeout(() => {
          navigate("/Product");
        }, 2000);
      })
      .catch((err) => {
        setError(err.response.data.message);
      });
  }
</script>

<!----------------------------- Layout Section ----------------------------->
<form on:submit|preventDefault={handleSubmit} class="form-signin">
  <h1 class="h3 mb-3 fw-normal" id="login-title">Login</h1>
  <div class="form-floating">
    <input
      type="email"
      class="form-control"
      id="floatingInput"
      placeholder="email address"
      name="emailAddress"
      bind:value={emailAddress}
    />
  </div>
  <div class="form-floating">
    <input
      type="password"
      class="form-control"
      id="floatingPassword-login"
      placeholder="password"
      name="password"
      bind:value={password}
    />
  </div>
  <button
    class="w-100 btn btn-lg btn-primary"
    id="submit-button-login"
    type="submit">Login</button
  >
  <Link className="signup-link" to="/Signup">Don't have an account? Signup</Link
  >
</form>

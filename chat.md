<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>Chatbot</title>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link rel="stylesheet" href="/assets/css/style1.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
</head>

<body>

  <!-- partial:index.partial.html -->
  <section class="msger">
    <header class="msger-header">
      <div class="msger-header-title">
        <i class="fas fa-bug"></i> Chatbot <i class="fas fa-bug"></i>
      </div>
    </header>

    <main class="msger-chat">
      <div class="msg left-msg">
        <div class="msg-img" style="background-image: url(https://lh3.googleusercontent.com/9Bhji6muyQEOIiAGIaKCH1PlpsT4PKQc4f1nzzMYWC4-VxVr5XjhZxDQfisTe8VPUx54cWrmvwdEaQ0yq0U5lXyNjNwFT9PVNsjbhZogu8VJhMOeuKUynWJ6ZWjKIllnhNWBcltPBoc--gPi3lu9C7GZ66mnR6espDOKgz6508bPkzt3iH2GaFcSvpBXli0kdmVx6wPuHmSbKhhez6hoiw8uiVShsTuiCRTZ1VSS7-LBco8OyoMt1IfDPMnP6JNF1iNSKAy9FA0yppG4baFPr8f0WIYCIF2DZUcD6T9iPby29WBQTrSAG7_L0Yi_PiHPod_HQfeeKVRf8tUHbqevcn4_RA3tgbwPUi2lZEH0d9BYHInwPj8KpXqc0W-gfxXEZTL1V3kHQY8VhE_k_3X2z9cKMBPU2SwSTeSEtFsvSCBz8-RLmtc3IlrzdefzI1TsxtGMGwlzVflkXDhMMwnw7fooStUAadoXRzMJhkItCMobHCcoLXwBz74NQXKCcxS0a2q5-yHvJHtCdcoXaITZ7hfy0XAXTZKdpt6QMoJf55P5v7NloIBAHQEjqyZOwDjW8AOlxyHcoxmBpj_VCKDEs-z-_ZheIgoWvbJcsdaZv2BU9d1i_cnb-36CrOTQD2yx-YCa8iuOKYH7Tp4Qm1F9_yJtE0C10nLvp31knMSr0nyRGlNwGpRLt845JfksETOzzrcWTjD5ecmt0LACOVrNyabWvs2T2-KT5-M_uMoiJjMc7VWpc1qWWEGRc-St-68DuxK35eBG-qRxxfrsOd5MvCveplPG0eOr7Iw=w791-h667-no?authuser=0)"></div>

        <div class="msg-bubble">
          <div class="msg-info">
            <div class="msg-info-name"> Tuấn Anh bot</div>
            <div class="msg-info-time">Just Now</div>
          </div>

          <div class="msg-text">
            Xin chào. Chào mừng đến với trang web của tôi
          </div>
        </div>
      </div>

    </main>

    <form class="msger-inputarea">
      <input type="text" class="msger-input" id="textInput" placeholder="Enter your message...">
      <button type="submit" class="msger-send-btn">Send</button>
    </form>
  </section>
  <!-- partial -->
  <script type="text/javascript">
    // STORE TOKEN INTO LOCALSTORAGE
    sessionStorage.setItem('action', 'default_action');
    sessionStorage.setItem('state', 0);
  </script>
  <script src='https://use.fontawesome.com/releases/v5.0.13/js/all.js'></script>
  <script>

    const msgerForm = get(".msger-inputarea");
    const msgerInput = get(".msger-input");
    const msgerChat = get(".msger-chat");

    
    // Icons made by Freepik from www.flaticon.com
    const BOT_IMG = "https://lh3.googleusercontent.com/9Bhji6muyQEOIiAGIaKCH1PlpsT4PKQc4f1nzzMYWC4-VxVr5XjhZxDQfisTe8VPUx54cWrmvwdEaQ0yq0U5lXyNjNwFT9PVNsjbhZogu8VJhMOeuKUynWJ6ZWjKIllnhNWBcltPBoc--gPi3lu9C7GZ66mnR6espDOKgz6508bPkzt3iH2GaFcSvpBXli0kdmVx6wPuHmSbKhhez6hoiw8uiVShsTuiCRTZ1VSS7-LBco8OyoMt1IfDPMnP6JNF1iNSKAy9FA0yppG4baFPr8f0WIYCIF2DZUcD6T9iPby29WBQTrSAG7_L0Yi_PiHPod_HQfeeKVRf8tUHbqevcn4_RA3tgbwPUi2lZEH0d9BYHInwPj8KpXqc0W-gfxXEZTL1V3kHQY8VhE_k_3X2z9cKMBPU2SwSTeSEtFsvSCBz8-RLmtc3IlrzdefzI1TsxtGMGwlzVflkXDhMMwnw7fooStUAadoXRzMJhkItCMobHCcoLXwBz74NQXKCcxS0a2q5-yHvJHtCdcoXaITZ7hfy0XAXTZKdpt6QMoJf55P5v7NloIBAHQEjqyZOwDjW8AOlxyHcoxmBpj_VCKDEs-z-_ZheIgoWvbJcsdaZv2BU9d1i_cnb-36CrOTQD2yx-YCa8iuOKYH7Tp4Qm1F9_yJtE0C10nLvp31knMSr0nyRGlNwGpRLt845JfksETOzzrcWTjD5ecmt0LACOVrNyabWvs2T2-KT5-M_uMoiJjMc7VWpc1qWWEGRc-St-68DuxK35eBG-qRxxfrsOd5MvCveplPG0eOr7Iw=w791-h667-no?authuser=0";
    const PERSON_IMG = "https://iconarchive.com/download/i84591/custom-icon-design/flatastic-4/User-blue.ico";
    const BOT_NAME = "    Tuấn Anh Bot";
    const PERSON_NAME = "you";

    msgerForm.addEventListener("submit", event => {
      event.preventDefault();

      const msgText = msgerInput.value;
      if (!msgText) return;

      appendMessage(PERSON_NAME, PERSON_IMG, "right", msgText);
      msgerInput.value = "";
      botResponse(msgText);
    });

    function appendMessage(name, img, side, text) {
      //   Simple solution for small apps
      const msgHTML = `
<div class="msg ${side}-msg">
  <div class="msg-img" style="background-image: url(${img})"></div>

  <div class="msg-bubble">
    <div class="msg-info">
      <div class="msg-info-name">${name}</div>
      <div class="msg-info-time">${formatDate(new Date())}</div>
    </div>

    <div class="msg-text">${text}</div>
  </div>
</div>
`;
      const msgHTML2 = `
<div class="msg ${side}-msg">
  <div class="msg-img" style="background-image: url(${img})"></div>

  <div class="msg-bubble">
    <div class="msg-info">
      <div class="msg-info-name">{{name1}}</div>
      <div class="msg-info-time">${formatDate(new Date())}</div>
    </div>

    <div class="msg-text">${text}</div>
  </div>
</div>
`;
      if (side == 'left') {
      msgerChat.insertAdjacentHTML("beforeend", msgHTML);}
      else {msgerChat.insertAdjacentHTML("beforeend", msgHTML2)}
      msgerChat.scrollTop += 500;
    }

    function botResponse(rawText) {
      let token = sessionStorage.getItem('accesstoken')
      let current_action = sessionStorage.getItem('action')
      let current_state = sessionStorage.getItem('state')
      $.get("/get", {accesstoken: token, msg: rawText ,action : current_action , state : current_state}).done(function (data) {
        console.log(rawText);
        console.log(data);
        console.log(data.action);
        console.log(data.state);
        console.log(data.res);
        const msgText = data.res;
        const recive_action =data.action;
        const recive_state = data.state;
        sessionStorage.setItem('action', recive_action);
        sessionStorage.setItem('state', recive_state);
        appendMessage(BOT_NAME, BOT_IMG, "left", msgText);

      }); 

    }


    // Utils
    function get(selector, root = document) {
      return root.querySelector(selector);
    }

    function formatDate(date) {
      const h = "0" + date.getHours();
      const m = "0" + date.getMinutes();

      return `${h.slice(-2)}:${m.slice(-2)}`;
    }



  </script>

</body>

</html>

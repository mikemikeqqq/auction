<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>虚拟现实拍卖实验</title>
    <style>
      /* ========== 通用样式 ========== */
      body {
        font-family: Arial, sans-serif;
        background-color: #f4f4f4;
        margin: 0;
        padding: 20px;
      }
      .container {
        max-width: 900px;
        margin: auto;
        background: #fff;
        padding: 20px;
        border-radius: 8px;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
      }
      h1, h2, h3 {
        text-align: center;
      }
      .button-group {
        margin-top: 20px;
        text-align: center;
      }
      button {
        padding: 10px 20px;
        margin: 5px;
        font-size: 16px;
        cursor: pointer;
      }
      input[type="number"],
      input[type="email"],
      input[type="text"],
      select {
        width: 200px;
        padding: 5px;
        margin: 10px 0;
      }
      .error {
        color: red;
      }
      .green-text {
        color: green;
        font-weight: bold;
      }
      .red-text {
        color: red;
        font-weight: bold;
      }
      .page {
        display: none;
      }
      .active {
        display: block;
      }
      
      /* ========== 图片预览修正样式 ========== */
      .image-slider {
        position: relative;
        width: 600px;
        height: 400px;
        margin: auto;
        text-align: center;
        border-radius: 10px;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #000;
      }
      .image-slider img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        border-radius: 10px;
      }
      .arrow {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background-color: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        padding: 15px;
        cursor: pointer;
        font-size: 24px;
        border-radius: 50%;
        z-index: 10;
      }
      .left {
        left: 10px;
      }
      .right {
        right: 10px;
      }
      .arrow:hover {
        background-color: rgba(0, 0, 0, 0.8);
      }
      
      /* ========== 页面内容居中 ========== */
      .auction-container {
        text-align: center;
        margin: 0 auto; 
        max-width: 700px;
      }
      #riskTest {
        text-align: center;
        max-width: 700px;
        margin: 0 auto;
      }
      
      /* ========== 出价历史记录样式 ========== */
      .bid-history {
        border: 1px solid #ccc;
        padding: 10px;
        margin-top: 20px;
        text-align: left;
      }
      .bid-history ul {
        list-style-type: none;
        padding: 0;
        margin: 0;
      }
      
      /* ========== 问卷量表样式 ========== */
      .question {
        margin-bottom: 20px;
      }
      .likert label {
        margin-right: 15px;
      }
    </style>
  </head>
  
<body>
  <!-- ========== 页面1：实验介绍与知情同意 ========== -->
  <div id="page1" class="container page active">
    <h1>一、实验介绍与知情同意书</h1>
    <p>
      感谢您抽出时间参与本研究。本实验旨在探讨现代技术对拍卖行为的影响，并将通过虚拟现实环境来模拟线上拍卖的情境。实验全程大约耗时 10 分钟，分为以下四个阶段：预览、模拟、竞拍和问卷。请您仔细阅读以下所有说明，并在确定理解和同意后继续进行实验。
    </p>
    <p>
      本实验属于学术研究，所得数据将被严格匿名化，仅用于科学研究和学术发表。您在任何时候都有权退出实验而无需提供理由。如果您对实验流程或隐私保护有任何疑问，请随时联系研究团队：<strong>minghao.li@nottingham.edu.cn</strong>。
    </p>
    <p>
      在本实验过程中，请想象您在一个线上拍卖网站上发现了一辆小型轿车并被它吸引，接下来您将通过竞拍方式尝试获得该车一定期限的使用权。实验结束后，您需要完成一份简短的调查问卷，以帮助我们了解您的决策过程与相关感受。<br>
      如果您仔细阅读说明并做出合理的竞价决策，您将获得相应的使用权奖励或收益。
    </p>
    
    <h2>二、实验流程介绍</h2>
    <p>
      第一阶段为<strong>预览阶段</strong>，您将通过一组预览对目标车辆进行基本的了解。  
      第二阶段为<strong>模拟阶段</strong>，系统会以示例或小测方式，让您熟悉竞拍界面与操作方法。  
      第三阶段为<strong>竞拍阶段</strong>，您将与其他匿名参与者竞争获得该车辆一定期限的使用权。每位参与者初始拥有 500,000 MU（虚拟代币，Monetary Unit）确保您在拍卖中有足够资金进行竞价。  
      第四阶段为<strong>问卷阶段</strong>，实验完成后，您将回答一份简短问卷，帮助我们了解您的决策体验和对该拍卖体验的看法。
    </p>
    
    <h2>三、拍卖与收益说明</h2>
    <p>
      竞拍时，您将被告知该拍品的评估价值。您需要根据自己对车辆实际价值的判断做出出价决策。车辆的实际价值将在拍卖结束后公布，且该车辆使用权的实际市场价值介于 150,000 MU 到 300,000 MU 之间，但在拍卖开始前您不会得知具体数值。 
    </p>
    <p>
      在拍卖中，您将与多个匿名竞拍者竞争该标的物。在正式开始前，您将经历一次短暂的模拟竞拍或测试环节，以确保您了解所有操作并熟悉界面。完成测试后，您才能进入实际拍卖。请保持注意力，并根据对车辆价值的判断及竞价策略合理出价。
    </p>
    <p>
      卖家设定了<strong>"立即购买"</strong>价格，当竞拍者的出价达到或超过提前设定并公开的"立即购买"价格时，系统将自动成交。<br>
      同时，卖家还设定了不公开的<strong>"保留价格"</strong>，若竞拍者的最终出价未能达到该保留价格，则竞拍将被视为无效并自动终止。
    </p>
    <p>
      <strong>起拍价格</strong>：本次拍卖的起拍价为 140,000 MU。<br>
      <strong>竞拍方式</strong>：本拍卖采用升价式拍卖，每次最低加价幅度为 5,000 MU，出价最长间隔为 30 秒。<br>
      <strong>竞拍结束条件</strong>：<br>
      - 无人再出价：如果所有竞标者都不愿继续加价，则拍卖立即结束。<br>
      - 达到封顶价格：如果竞价达到系统设定的最高封顶价格，拍卖自动结束，当前最高出价者直接成交。<br>
      最高出价者将获得该车辆一定期限的使用权，并按最终出价支付竞拍价格。
    </p>
    <p>
      <strong>奖励计算</strong><br>
      拍卖结束后，系统将公布该车辆的真实市场价值（介于 150,000 MU 至 300,000 MU 之间），并按照以下公式计算您的最终实验收益：<br>
      <strong>您的最终收益 = 该汽车的真实价值 - 您的最终出价</strong>。<br>
      您的收益将按照 10,000 MU = 5 RMB 的兑换率转换为现金奖励。
    </p>
    <p>
      示例：假设您最后出价为 240,000 MU，而该车的真实价值为 250,000 MU，则您的盈利为 10,000 MU，最终可获得 5 RMB 现金奖励。
    </p>
    <p>
      如果您在拍卖过程中中途退出，则本场拍卖不计入您的收益。拍卖结束后，系统将根据您的决策自动计算总收益，并按照兑换率支付现金奖励。
    </p>   
    <h2>五、数据隐私与退出权</h2>
    <p>
      您在实验中产生的所有数据（包括决策与生理数据，如有记录）均将严格匿名化并加密处理，仅用于学术研究与分析，绝不外泄。您可随时退出实验，无需说明理由。如有疑问，请联系 <strong>minghao.li@nottingham.edu.cn</strong>。
    </p>
    
    <h2>六、声明与开始</h2>
    <p>
      点击"我已阅读并同意"按钮即表示您理解实验内容、目的及可能带来的收益与风险，并自愿参加本次实验。
    </p>
    <hr>
    <h2>测验：请确认您理解拍卖规则</h2>
    <p>Q1: 如果您用 210,000 MU 成功竞得一辆汽车，而该汽车最终价值为 230,000 MU，您的净收益是多少？</p>
    <form id="quizForm">
      <label><input type="radio" name="answer" value="20,000"> 20,000 MU</label><br>
      <label><input type="radio" name="answer" value="30,000"> 30,000 MU</label><br>
      <label><input type="radio" name="answer" value="40,000"> 40,000 MU</label><br>
      <label><input type="radio" name="answer" value="50,000"> 50,000 MU</label><br>
      <span id="quizError" class="error"></span>
      <br>
      <div class="button-group">
        <button type="button" id="agreeButton">同意并继续</button>
        <button type="button" id="disagreeButton">不同意</button>
      </div>
    </form>
  </div>
  
  <!-- ========== 页面2：VR vs. Non-VR预览 ========== -->
  <div id="page2" class="container page">
    <h1>汽车预览</h1>
    <p>请想象您在一个线上拍卖网站上发现了这辆小型轿车并被其吸引。</p>
    <p>请您花费至少两分钟仔细预览该款汽车，倒计时结束后进入模拟竞拍环节。</p>
    <div id="previewArea"></div>
    <div class="code" id="uniqueCode"></div>
    <p>请等待预览时间结束： <span id="countdownTimer">2</span> 秒</p>
    <div class="button-group">
      <button id="nextButtonPage2" disabled>下一步</button>
    </div>
  </div>
  
  <!-- ========== 页面3：模拟拍卖 ========== -->
  <div id="page3" class="container page">
    <h1>模拟拍卖</h1>
    <p>提示：本页面中显示的保留价格、立即购买价格、起拍价格及评估价值均为模拟数据，真实拍卖中数值可能会有所变化。</p>
    <div class="auction-container">
      <div class="product-info">
        <h2>拍卖商品：汽车使用权</h2>
        <h2>评估价值：150,000-300,000 MU</h2>
        <p>起拍价：140,000 MU</p>
        <p>立即购买价格：310,000 MU</p>
        <p>最小加价：5,000 MU</p>
      </div>
      <div class="bid-info">
        <p>当前最高出价：<span id="currentBid_sim">135,000</span> MU</p>
        <p>最高出价者：<span id="highestBidder_sim">无</span></p>
        <p>您的出价：<input type="number" id="userBid_sim" step="5000" min="140000" max="500000" value="140000"> MU</p>
        <button id="placeBid_sim">出价</button>
        <button id="buyNow_sim">立即购买</button>
      </div>
      <div class="bid-history" id="bidHistory_sim">
        <h3>出价历史记录</h3>
        <ul id="bidHistoryList_sim"></ul>
      </div>
      <div class="timer">
        <p>剩余时间：<span id="timeLeft_sim">30</span> 秒</p>
      </div>
      <div class="result">
        <p id="resultMessage_sim"></p>
      </div>
      <div class="button-group">
        <button id="nextButtonPage3" style="display: none;">下一步</button>
      </div>
    </div>
  </div>
  
  <!-- ========== 页面4：正式拍卖 ========== -->
  <div id="page4" class="container page">
    <h1>正式拍卖</h1>
    <p>现在进入正式拍卖环节，请根据预览及您的判断为该汽车使用权出价。若竞拍成功，您将获得车辆使用权，并按最终出价支付拍卖价格。</p>
    <div class="auction-container">
      <div class="product-info">
        <h2>拍卖商品：汽车使用权</h2>
        <h2>评估价值：150,000-300,000 MU</h2>
        <p>起拍价：140,000 MU</p>
        <p>立即购买价格：300,000 MU</p>
        <p>最小加价：5,000 MU</p>
      </div>
      <div class="bid-info">
        <p>当前最高出价：<span id="currentBid_formal">140,000</span> MU</p>
        <p>最高出价者：<span id="highestBidder_formal">无</span></p>
        <p>您的出价：<input type="number" id="userBid_formal" step="5000" min="140000" max="500000" value="140000"> MU</p>
        <button id="placeBid_formal">出价</button>
        <button id="buyNow_formal">立即购买</button>
      </div>
      <div class="bid-history" id="bidHistory_formal">
        <h3>出价历史记录</h3>
        <ul id="bidHistoryList_formal"></ul>
      </div>
      <div class="timer">
        <p>剩余时间：<span id="timeLeft_formal">30</span> 秒</p>
      </div>
      <div class="result">
        <p id="resultMessage_formal"></p>
      </div>
      <!-- 以下区域拍卖结束后再显示 -->
      <div class="final-result" id="finalResult" style="display: none;">
        <h2>拍卖结束</h2>
        <p>您的最终出价：<span id="finalBid"></span> MU</p>
        <p>车辆真实价值：<span id="realValue"></span> MU</p>
        <p id="profitParagraph">您的虚拟收益：<span id="virtualProfit"></span> MU</p>
        <p id="cashParagraph">转换成现金奖励：<span id="cashReward"></span> RMB</p>
        <div class="button-group">
          <button id="nextButtonPage4" style="display: none;">下一步</button>
        </div>
      </div>
    </div>
  </div>
  
  <!-- 
    ========== 修改点 ==========
    原先的问卷 (page5) 与风险测试 (page6) 及收益 (page7) 整合在一起。
    现在根据您的需求，将问卷分成5页（page5 ~ page9），并把风险测试放到page10，最终收益页放到page11。
    下方是5页问卷，每页都要检查漏选，漏选时禁止进入下一页。
   -->
  
  <!-- ========== 问卷 第1页 (page5) ========== -->
  <div id="page5" class="container page">
    <h1>问卷调查（第1页）</h1>
    <form id="surveyPage1">
      <div class="question">
        <p>1. 在预览这辆车后，我感觉它像是属于我的。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q1" value="1" required> 1</label>
          <label><input type="radio" name="q1" value="2"> 2</label>
          <label><input type="radio" name="q1" value="3"> 3</label>
          <label><input type="radio" name="q1" value="4"> 4</label>
          <label><input type="radio" name="q1" value="5"> 5</label>
          <label><input type="radio" name="q1" value="6"> 6</label>
          <label><input type="radio" name="q1" value="7"> 7</label>
        </div>
      </div>
      <div class="question">
        <p>2. 在预览这辆车后，我感觉我对它有一种强烈的拥有感。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q2" value="1" required> 1</label>
          <label><input type="radio" name="q2" value="2"> 2</label>
          <label><input type="radio" name="q2" value="3"> 3</label>
          <label><input type="radio" name="q2" value="4"> 4</label>
          <label><input type="radio" name="q2" value="5"> 5</label>
          <label><input type="radio" name="q2" value="6"> 6</label>
          <label><input type="radio" name="q2" value="7"> 7</label>
        </div>
      </div>
      <div class="question">
        <p>3. 观看完预览后，我觉得我已经拥有了这辆车。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q3" value="1" required> 1</label>
          <label><input type="radio" name="q3" value="2"> 2</label>
          <label><input type="radio" name="q3" value="3"> 3</label>
          <label><input type="radio" name="q3" value="4"> 4</label>
          <label><input type="radio" name="q3" value="5"> 5</label>
          <label><input type="radio" name="q3" value="6"> 6</label>
          <label><input type="radio" name="q3" value="7"> 7</label>
        </div>
      </div>
      <div class="button-group">
        <button type="submit">下一页</button>
      </div>
      <span id="surveyPage1Error" class="error"></span>
    </form>
  </div>

  <!-- ========== 问卷 第2页 (page6) ========== -->
  <div id="page6" class="container page">
    <h1>问卷调查（第2页）</h1>
    <form id="surveyPage2">
      <div class="question">
        <p>4. 在参与在线拍卖时，拍卖平台提供的拍品预览帮助我做出更好的决策。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q4" value="1" required>1</label>
          <label><input type="radio" name="q4" value="2">2</label>
          <label><input type="radio" name="q4" value="3">3</label>
          <label><input type="radio" name="q4" value="4">4</label>
          <label><input type="radio" name="q4" value="5">5</label>
          <label><input type="radio" name="q4" value="6">6</label>
          <label><input type="radio" name="q4" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>5. 在参与在线拍卖时，当我对某些信息不理解时，拍品预览让我更难做出决策。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q5" value="1" required>1</label>
          <label><input type="radio" name="q5" value="2">2</label>
          <label><input type="radio" name="q5" value="3">3</label>
          <label><input type="radio" name="q5" value="4">4</label>
          <label><input type="radio" name="q5" value="5">5</label>
          <label><input type="radio" name="q5" value="6">6</label>
          <label><input type="radio" name="q5" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>6. 在参与在线拍卖时，拍品预览会减慢我的决策过程。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q6" value="1" required>1</label>
          <label><input type="radio" name="q6" value="2">2</label>
          <label><input type="radio" name="q6" value="3">3</label>
          <label><input type="radio" name="q6" value="4">4</label>
          <label><input type="radio" name="q6" value="5">5</label>
          <label><input type="radio" name="q6" value="6">6</label>
          <label><input type="radio" name="q6" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>7. 在参与在线拍卖时，拍品预览让我更容易做出决策。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q7" value="1" required>1</label>
          <label><input type="radio" name="q7" value="2">2</label>
          <label><input type="radio" name="q7" value="3">3</label>
          <label><input type="radio" name="q7" value="4">4</label>
          <label><input type="radio" name="q7" value="5">5</label>
          <label><input type="radio" name="q7" value="6">6</label>
          <label><input type="radio" name="q7" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>8. 在参与在线拍卖时，我通过拍品预览能轻松理解相关信息。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q8" value="1" required>1</label>
          <label><input type="radio" name="q8" value="2">2</label>
          <label><input type="radio" name="q8" value="3">3</label>
          <label><input type="radio" name="q8" value="4">4</label>
          <label><input type="radio" name="q8" value="5">5</label>
          <label><input type="radio" name="q8" value="6">6</label>
          <label><input type="radio" name="q8" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>9. 拍品预览帮助我快速做出决策。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q9" value="1" required>1</label>
          <label><input type="radio" name="q9" value="2">2</label>
          <label><input type="radio" name="q9" value="3">3</label>
          <label><input type="radio" name="q9" value="4">4</label>
          <label><input type="radio" name="q9" value="5">5</label>
          <label><input type="radio" name="q9" value="6">6</label>
          <label><input type="radio" name="q9" value="7">7</label>
        </div>
      </div>
      <div class="button-group">
        <button type="submit">下一页</button>
      </div>
      <span id="surveyPage2Error" class="error"></span>
    </form>
  </div>
  
  <!-- ========== 问卷 第3页 (page7) ========== -->
  <div id="page7" class="container page">
    <h1>问卷调查（第3页）</h1>
    <form id="surveyPage3">
      <div class="question">
        <p>10. 该拍卖平台的拍品预览提供了关于拍品的准确信息。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q10" value="1" required>1</label>
          <label><input type="radio" name="q10" value="2">2</label>
          <label><input type="radio" name="q10" value="3">3</label>
          <label><input type="radio" name="q10" value="4">4</label>
          <label><input type="radio" name="q10" value="5">5</label>
          <label><input type="radio" name="q10" value="6">6</label>
          <label><input type="radio" name="q10" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>11. 总体而言，我认为拍品预览提供了有用的信息。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q11" value="1" required>1</label>
          <label><input type="radio" name="q11" value="2">2</label>
          <label><input type="radio" name="q11" value="3">3</label>
          <label><input type="radio" name="q11" value="4">4</label>
          <label><input type="radio" name="q11" value="5">5</label>
          <label><input type="radio" name="q11" value="6">6</label>
          <label><input type="radio" name="q11" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>12. 拍品预览提供了关于拍品的及时信息。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q12" value="1" required>1</label>
          <label><input type="radio" name="q12" value="2">2</label>
          <label><input type="radio" name="q12" value="3">3</label>
          <label><input type="radio" name="q12" value="4">4</label>
          <label><input type="radio" name="q12" value="5">5</label>
          <label><input type="radio" name="q12" value="6">6</label>
          <label><input type="radio" name="q12" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>13. 拍品预览提供了可靠的信息。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q13" value="1" required>1</label>
          <label><input type="radio" name="q13" value="2">2</label>
          <label><input type="radio" name="q13" value="3">3</label>
          <label><input type="radio" name="q13" value="4">4</label>
          <label><input type="radio" name="q13" value="5">5</label>
          <label><input type="radio" name="q13" value="6">6</label>
          <label><input type="radio" name="q13" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>14. 当我在拍卖中做出决策时，拍品预览提供了充分的信息。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q14" value="1" required>1</label>
          <label><input type="radio" name="q14" value="2">2</label>
          <label><input type="radio" name="q14" value="3">3</label>
          <label><input type="radio" name="q14" value="4">4</label>
          <label><input type="radio" name="q14" value="5">5</label>
          <label><input type="radio" name="q14" value="6">6</label>
          <label><input type="radio" name="q14" value="7">7</label>
        </div>
      </div>
      <div class="button-group">
        <button type="submit">下一页</button>
      </div>
      <span id="surveyPage3Error" class="error"></span>
    </form>
  </div>
  
  <!-- ========== 问卷 第4页 (page8) ========== -->
  <div id="page8" class="container page">
    <h1>问卷调查（第4页）</h1>
    <form id="surveyPage4">
      <div class="question">
        <p>15. 基于拍品预览，您对拍品的功能表现有多确定？（1=完全不确定 ~ 7=非常确定）</p>
        <div class="likert">
          <label><input type="radio" name="q15" value="1" required>1</label>
          <label><input type="radio" name="q15" value="2">2</label>
          <label><input type="radio" name="q15" value="3">3</label>
          <label><input type="radio" name="q15" value="4">4</label>
          <label><input type="radio" name="q15" value="5">5</label>
          <label><input type="radio" name="q15" value="6">6</label>
          <label><input type="radio" name="q15" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>16. 基于拍品预览，您对拍品功能表现的判断有多容易？（1=很难判断 ~ 7=很容易判断）</p>
        <div class="likert">
          <label><input type="radio" name="q16" value="1" required>1</label>
          <label><input type="radio" name="q16" value="2">2</label>
          <label><input type="radio" name="q16" value="3">3</label>
          <label><input type="radio" name="q16" value="4">4</label>
          <label><input type="radio" name="q16" value="5">5</label>
          <label><input type="radio" name="q16" value="6">6</label>
          <label><input type="radio" name="q16" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>17. 基于拍品预览，我觉得拍品可能会……（1=无法正常工作 ~ 7=正常工作）</p>
        <div class="likert">
          <label><input type="radio" name="q17" value="1" required>1</label>
          <label><input type="radio" name="q17" value="2">2</label>
          <label><input type="radio" name="q17" value="3">3</label>
          <label><input type="radio" name="q17" value="4">4</label>
          <label><input type="radio" name="q17" value="5">5</label>
          <label><input type="radio" name="q17" value="6">6</label>
          <label><input type="radio" name="q17" value="7">7</label>
        </div>
      </div>
      <div class="button-group">
        <button type="submit">下一页</button>
      </div>
      <span id="surveyPage4Error" class="error"></span>
    </form>
  </div>
  
  <!-- ========== 问卷 第5页 (page9) ========== -->
  <div id="page9" class="container page">
    <h1>问卷调查（第5页）</h1>
    <form id="surveyPage5">
      <div class="question">
        <p>18. 您之前是否参与过在线拍卖？(是或否）</p>
        <label><input type="radio" name="q18" value="是" required> 是</label>
        <label><input type="radio" name="q18" value="否"> 否</label>
      </div>
      <div class="question">
        <p>19. 在拍品预览页面中，我使用了VR预览。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q19" value="1" required>1</label>
          <label><input type="radio" name="q19" value="2">2</label>
          <label><input type="radio" name="q19" value="3">3</label>
          <label><input type="radio" name="q19" value="4">4</label>
          <label><input type="radio" name="q19" value="5">5</label>
          <label><input type="radio" name="q19" value="6">6</label>
          <label><input type="radio" name="q19" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>20. 您近期准备购入一辆汽车。（1=非常不同意 ~ 7=非常同意）</p>
        <div class="likert">
          <label><input type="radio" name="q20" value="1" required>1</label>
          <label><input type="radio" name="q20" value="2">2</label>
          <label><input type="radio" name="q20" value="3">3</label>
          <label><input type="radio" name="q20" value="4">4</label>
          <label><input type="radio" name="q20" value="5">5</label>
          <label><input type="radio" name="q20" value="6">6</label>
          <label><input type="radio" name="q20" value="7">7</label>
        </div>
      </div>
      <div class="question">
        <p>21. 请问您在拍卖前预览的车辆车身颜色是什么？</p>
        <select name="q21" required>
          <option value="">请选择</option>
          <option value="1. 白色和紫色">1. 白色和紫色</option>
          <option value="2. 灰色和银色">2. 灰色和银色</option>
          <option value="3. 红色和紫色">3. 红色和紫色</option>
          <option value="4. 蓝色和白色">4. 蓝色和白色</option>
          <option value="5. 紫色和红色">5. 紫色和红色</option>
        </select>
      </div>
      <div class="button-group">
        <button type="submit">提交问卷</button>
      </div>
      <span id="surveyPage5Error" class="error"></span>
    </form>
  </div>
  
  <!-- ========== 页面10：风险偏好彩票测试和支付宝确认 ========== -->
  <div id="page10" class="container page">
    <h1>最终彩票游戏与收益汇总</h1>
    <p>
      最后，在结束测试前，您还需要完成一组包括十张彩票的选择测试。每组测试中，您将看到两张彩票，每张彩票对应不同的获奖概率和奖金。<br>
      请根据您的个人喜好选择您更偏好的选项。结束后，系统将从您选择的十张彩票中随机抽取一张，并根据该彩票的概率自动计算您应得的奖金金额。
    </p>
    <div id="riskTest">
      <p id="riskQuestion">问题加载中...</p>
      <div id="riskOptions" class="option-group"></div>
      <p id="riskProgress">0/10</p>
      <div class="button-group">
        <button id="nextRiskButton" disabled>下一题</button>
      </div>
      <p id="lotteryResult" style="font-weight: bold; color: blue;"></p>
      <!-- 彩票结果后显示收益汇总和支付宝输入区域 -->
      <div id="finalPaymentArea" style="display: none;">
        <h2>收益汇总</h2>
        <p id="finalMessage"></p>
        <div id="alipayInputArea">
          <p>请输入您的支付宝账号：</p>
          <input type="email" id="alipayAccount" placeholder="请输入支付宝账号">
          <button id="submitAlipay">提交支付宝账号</button>
        </div>
        <div id="alipayConfirmArea" style="display: none;">
          <p>您输入的支付宝账号是：<strong><span id="displayAlipay"></span></strong></p>
          <p>请确认该账号是否正确？</p>
          <button id="confirmAlipay">正确</button>
          <button id="editAlipay">重新编辑</button>
        </div>
        <div id="finalThankYou" style="display: none;">
          <h2>实验完成</h2>
          <p>感谢您参与本次实验！</p>
          <p id="finalPaymentMsg"></p>
          <p>研究者将在审核数据后 7 个工作日内把相应的实验奖励支付到您提供的支付宝账号中。</p>
        </div>
      </div>
    </div>
  </div>
  
  <script>
    /********** 全局变量及活动监测 **********/
    let participantId = "P" + Math.floor(1000 + Math.random() * 9000);
    let pageTimes = {};
    let currentPage = null;
    let startTime = null;
    // 活动日志记录
    let activityLog = {
      bidHistoryFormal: [],
      bidHistorySim: [],
      surveyResponses: {},
      riskResponses: [],
      immediatePurchase: false,
      finalWinner: false,    // ========== 修改点：标记是否为最高出价者
      auctionProfit: 0,
      lotteryBonus: 0,
      alipay: ""
    };
    
    function enterPage(pageId) {
      if (currentPage) {
        let endTime = new Date();
        pageTimes[currentPage] = ((endTime - startTime) / 1000).toFixed(1);
      }
      currentPage = pageId;
      startTime = new Date();
    }
    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
      document.getElementById(pageId).classList.add('active');
      enterPage(pageId);
    }
    window.addEventListener("beforeunload", function () {
      pageTimes[currentPage] = ((new Date() - startTime) / 1000).toFixed(1);
      console.log("页面停留时间记录：", pageTimes);
    });
    
    /********** 页面1：实验介绍与知情同意 **********/
    document.getElementById('agreeButton').addEventListener('click', function(){
      var selected = document.querySelector('input[name="answer"]:checked');
      if (!selected) {
        document.getElementById('quizError').textContent = "请先选择一个答案。";
        return;
      }
      if (selected.value !== "20,000") {
        document.getElementById('quizError').textContent = "回答错误，请仔细阅读规则并重新作答。";
        return;
      }
      showPage('page2');
    });
    document.getElementById('disagreeButton').addEventListener('click', function(){
      alert("您已选择退出实验，感谢您的时间！");
      window.location.href = "about:blank";
    });
    
    /********** 页面2：VR vs. Non-VR预览 **********/
    (function(){
      var group = (Math.random() < 0.5) ? "VR" : "NonVR";
      var randomNum = Math.floor(1000 + Math.random() * 9000);
      var uniqueCode = (group === "VR") ? "VR" + randomNum : "NOAR" + randomNum;
      localStorage.setItem("group", group);
      localStorage.setItem("uniqueCode", uniqueCode);
      document.getElementById("uniqueCode").textContent = "您的拍卖编码：" + uniqueCode;
      
      var previewArea = document.getElementById("previewArea");
      if (group === "VR") {
        previewArea.innerHTML = `
          <div style="text-align: center;">
            <h2>汽车 3D 预览</h2>
            <p>点击下方按钮打开 3D 预览。该预览将在新标签页打开。</p>
            <a href="https://www.faradayfuturecn.com/cn/3D-tour/" target="_blank" rel="noopener noreferrer">
              <button style="padding: 10px 20px; font-size: 16px; cursor: pointer;">打开 3D 预览</button>
            </a>
          </div>
        `;
      } else {
        previewArea.innerHTML = `
          <div class="image-slider">
            <button class="arrow left" onclick="prevImage()">&#10094;</button>
            <img id="sliderImage" src="https://i.postimg.cc/JzpskGN4/F6.jpg" alt="Image Preview">
            <button class="arrow right" onclick="nextImage()">&#10095;</button>
          </div>
        `;
      }
      
      var countdown = 2;
      var countdownElement = document.getElementById("countdownTimer");
      var nextButtonPage2 = document.getElementById("nextButtonPage2");
      nextButtonPage2.disabled = true;
      var timerInterval = setInterval(function(){
        countdown--;
        countdownElement.textContent = countdown;
        if (countdown <= 0) {
          clearInterval(timerInterval);
          nextButtonPage2.disabled = false;
          countdownElement.textContent = "0";
        }
      }, 1000);
    })();
    
    document.getElementById('nextButtonPage2').addEventListener('click', function(){
      showPage('page3');
    });
    
    var imageIndex = 0;
    var images = [
      "https://i.postimg.cc/fTjtMHkd/F1.jpg",
      "https://i.postimg.cc/L5F5pfpv/F2.jpg",
      "https://i.postimg.cc/Bvytmk7r/F3.jpg",
      "https://i.postimg.cc/9fzrtCbP/F4.jpg",
      "https://i.postimg.cc/524HywFR/F5.jpg",
      "https://i.postimg.cc/JzpskGN4/F6.jpg"
    ];
    function showImage(index) {
      var sliderImage = document.getElementById("sliderImage");
      if (sliderImage) {
        sliderImage.src = images[index];
      }
    }
    function prevImage() {
      if (imageIndex > 0) {
        imageIndex--;
        showImage(imageIndex);
      }
    }
    function nextImage() {
      if (imageIndex < images.length - 1) {
        imageIndex++;
        showImage(imageIndex);
      }
    }
    
    /********** 页面3：模拟拍卖 **********/
    (function(){
      let currentBid = 135000;
      let timeLeft = 30;
      let highestBidder = "无";
      let auctionStarted = false;
      let timer;
      const reservePrice_sim = 155000;   // 隐藏保留价（模拟用）
      const buyNowPrice_sim = 310000;   
      const botMaxBid = 500000;
      const botMinIncrease = 5000;
      const botReactionDelay = [2000, 4000, 6000];
      
      const currentBidElement = document.getElementById('currentBid_sim');
      const userBidElement = document.getElementById('userBid_sim');
      const placeBidButton = document.getElementById('placeBid_sim');
      const buyNowButton = document.getElementById('buyNow_sim');
      const highestBidderElement = document.getElementById('highestBidder_sim');
      const timeLeftElement = document.getElementById('timeLeft_sim');
      const resultMessageElement = document.getElementById('resultMessage_sim');
      const nextButton = document.getElementById('nextButtonPage3');
      const bidHistoryList = document.getElementById('bidHistoryList_sim');
      
      function updateBidHistory(bid, bidder) {
        let li = document.createElement('li');
        if (bidder === "您") li.classList.add("green-text");
        if (bidder === "匿名竞标者") li.classList.add("red-text");
        li.textContent = bidder + "： " + bid + " MU";
        bidHistoryList.appendChild(li);
        activityLog.bidHistorySim.push({bid: bid, bidder: bidder, time: new Date().toISOString()});
      }
      
      function updateBuyNowButton() {
        if (currentBid >= buyNowPrice_sim) {
          buyNowButton.disabled = true;
        } else {
          buyNowButton.disabled = false;
        }
      }
      
      function startAuction() {
        timer = setInterval(() => {
          timeLeft--;
          timeLeftElement.textContent = timeLeft;
          if (timeLeft <= 0) {
            clearInterval(timer);
            endAuction();
          }
        }, 1000);
      }
      
      // ========== 修改点：结束时若有人类参与者拍下，提示恭喜信息 ==========
      function endAuction() {
        userBidElement.disabled = true;
        placeBidButton.disabled = true;
        buyNowButton.disabled = true;
        
        // 判断是否达到保留价
        if(currentBid < reservePrice_sim) {
          resultMessageElement.textContent = `拍卖结束！最终成交价为 ${currentBid} MU，最高出价者：${highestBidder}。由于成交价没有达到保留价格，所以该次竞拍无效。`;
        } else {
          if (highestBidder === "您") {
            resultMessageElement.textContent = `拍卖结束，恭喜您拍得此车辆的使用权！(模拟阶段)`;
          } else {
            resultMessageElement.textContent = `拍卖结束！最终成交价为 ${currentBid} MU，最高出价者：${highestBidder}。`;
          }
        }
        nextButton.style.display = "block";
      }
      
      function updateHighestBidder(name, colorClass) {
        highestBidder = name;
        highestBidderElement.textContent = highestBidder;
        highestBidderElement.className = colorClass;
      }
      
      function botBid() {
        let botBidValue = currentBid + botMinIncrease;
        if (botBidValue <= botMaxBid) {
          setTimeout(() => {
            currentBid = botBidValue;
            currentBidElement.textContent = currentBid;
            updateHighestBidder("匿名竞标者", "red-text");
            resultMessageElement.textContent = "匿名竞标者已出价";
            updateBidHistory(currentBid, "匿名竞标者");
            updateBuyNowButton();
            if (!auctionStarted) {
              auctionStarted = true;
              startAuction();
            } else {
              timeLeft = 30;
            }
          }, botReactionDelay[Math.floor(Math.random() * botReactionDelay.length)]);
        }
      }
      
      placeBidButton.addEventListener('click', () => {
        const userBid = parseInt(userBidElement.value);
        if (userBid > 500000) {
          resultMessageElement.textContent = "您的虚拟货币仅有500000 MU，请输入不超过500000 MU的出价。";
          return;
        }
        
        // ========== 修改点：若出价>=buyNowPrice_sim，立即成交（模拟环节）==========
        if (userBid >= buyNowPrice_sim) {
          clearInterval(timer);
          currentBid = buyNowPrice_sim;
          currentBidElement.textContent = currentBid;
          updateHighestBidder("您", "green-text");
          resultMessageElement.textContent = `拍卖结束，恭喜您拍得此车辆的使用权！(模拟阶段)`;
          updateBidHistory(currentBid, "您（出价超立即购）");
          userBidElement.disabled = true;
          placeBidButton.disabled = true;
          buyNowButton.disabled = true;
          nextButton.style.display = "block";
          return;
        }
        
        if (userBid >= currentBid + botMinIncrease) {
          currentBid = userBid;
          currentBidElement.textContent = currentBid;
          updateHighestBidder("您", "green-text");
          resultMessageElement.textContent = "您已成功出价！";
          updateBidHistory(currentBid, "您");
          updateBuyNowButton();
          if (!auctionStarted) {
            auctionStarted = true;
            startAuction();
          } else {
            timeLeft = 30;
          }
          botBid();
        } else {
          resultMessageElement.textContent = '您的出价必须比当前价格高至少 5000 MU。';
        }
      });
      
      buyNowButton.addEventListener('click', () => {
        if(confirm("您是否确定以 310,000 MU 立即购买？")) {
          clearInterval(timer);
          currentBid = buyNowPrice_sim;
          currentBidElement.textContent = currentBid;
          updateHighestBidder("您", "green-text");
          resultMessageElement.textContent = `拍卖结束，恭喜您拍得此车辆的使用权！(模拟阶段)`;
          updateBidHistory(buyNowPrice_sim, "您（立即购买）");
          userBidElement.disabled = true;
          placeBidButton.disabled = true;
          buyNowButton.disabled = true;
          nextButton.style.display = "block";
        }
      });
      
      nextButton.addEventListener('click', function(){
        showPage('page4');
      });
    })();
    
    /********** 页面4：正式拍卖 **********/
    (function(){
      let currentBid = 135000;
      let timeLeft = 30;
      let highestBidder = "无";
      let auctionStarted = false;
      let timer;
      const fixedCarValueMU = 245900; // 车辆真实价值（示例）
      const conversionFactor = 0.0005; // 1 MU = 0.0005 RMB
      const reservePrice_formal = 150000; 
      const buyNowPrice_formal = 300000;
      const botMaxBid = 500000; 
      const botMinIncrease = 5000;
      const botReactionDelay = [2000, 4000, 6000];
      
      const currentBidElement = document.getElementById('currentBid_formal');
      const userBidElement = document.getElementById('userBid_formal');
      const placeBidButton = document.getElementById('placeBid_formal');
      const buyNowButton = document.getElementById('buyNow_formal');
      const highestBidderElement = document.getElementById('highestBidder_formal');
      const timeLeftElement = document.getElementById('timeLeft_formal');
      const resultMessageElement = document.getElementById('resultMessage_formal');
      const finalResultDiv = document.getElementById('finalResult');
      const finalBidElement = document.getElementById('finalBid');
      const realValueElement = document.getElementById('realValue');
      const virtualProfitElement = document.getElementById('virtualProfit');
      const cashRewardElement = document.getElementById('cashReward');
      const nextButton = document.getElementById('nextButtonPage4');
      const bidHistoryList = document.getElementById('bidHistoryList_formal');
      
      function updateBidHistory(bid, bidder) {
        let li = document.createElement('li');
        if (bidder === "您") li.classList.add("green-text");
        if (bidder === "匿名竞标者") li.classList.add("red-text");
        li.textContent = bidder + "： " + bid + " MU";
        bidHistoryList.appendChild(li);
        activityLog.bidHistoryFormal.push({bid: bid, bidder: bidder, time: new Date().toISOString()});
      }
      
      function updateBuyNowButton_formal() {
        if(currentBid >= buyNowPrice_formal) {
          buyNowButton.disabled = true;
        } else {
          buyNowButton.disabled = false;
        }
      }
      
      function startAuction() {
        timer = setInterval(() => {
          timeLeft--;
          timeLeftElement.textContent = timeLeft;
          if (timeLeft <= 0) {
            clearInterval(timer);
            endAuction();
          }
        }, 1000);
      }
      
      // ========== 修改点：正式拍卖结束后根据您要求的逻辑计算收益 ==========
      function endAuction() {
        userBidElement.disabled = true;
        placeBidButton.disabled = true;
        buyNowButton.disabled = true;
        
        // 判断是否达到保留价
        if (currentBid < reservePrice_formal) {
          resultMessageElement.textContent = `拍卖结束！最终成交价为 ${currentBid} MU，最高出价者：${highestBidder}。由于成交价没有达到保留价格，所以该次竞拍无效。`;
          // 拍卖收益 = 0，因为未达到保留价
          activityLog.auctionProfit = 0;
          // 若最高出价者是您，但价低于保留价，一样无效，不算您拍得
          activityLog.finalWinner = false;
        } else {
          // 拍卖有效（达到保留价）
          if (highestBidder === "您") {
            resultMessageElement.textContent = `拍卖结束，恭喜您拍得此车辆的使用权！`;
            // 按您最新说明：若成功拍得车辆，则仅获得 50 元补偿（概念车无法驾驶）
            // 即拍卖部分固定为 50 RMB；虚拟收益部分仅作展示
            activityLog.finalWinner = true;
            // 这里的auctionProfit先按价值-出价算，但实际不再折算为现金；只给固定50
            activityLog.auctionProfit = (fixedCarValueMU - currentBid);
          } else {
            resultMessageElement.textContent = `拍卖结束！最终成交价为 ${currentBid} MU，最高出价者：${highestBidder}。`;
            // 修正：即使未拍得，只要成交价高于保留价，仍应计算虚拟收益
            activityLog.auctionProfit = (fixedCarValueMU - currentBid);
            activityLog.finalWinner = false;
          }
        }
        
        finalResultDiv.style.display = "block";
        finalBidElement.textContent = currentBid;
        realValueElement.textContent = fixedCarValueMU;
        
        // 修改点1：如果人类参与者成功拍得，隐藏虚拟收益和现金奖励显示
        if (highestBidder === "您") {
          document.getElementById('profitParagraph').style.display = "none";
          document.getElementById('cashParagraph').style.display = "none";
        } else {
          // 展示虚拟收益（传统公式），但实际发放时遵循新补偿逻辑
          virtualProfitElement.textContent = activityLog.auctionProfit;
          let cashReward = (activityLog.auctionProfit / 10000 * 5).toFixed(2);
          cashRewardElement.textContent = cashReward;
        }
        
        nextButton.style.display = "block";
      }
      
      function updateHighestBidder(name, colorClass) {
        highestBidder = name;
        highestBidderElement.textContent = highestBidder;
        highestBidderElement.className = colorClass;
      }
      
      function botBid() {
        let botBidValue = currentBid + botMinIncrease;
        if (botBidValue <= botMaxBid) {
          setTimeout(() => {
            currentBid = botBidValue;
            currentBidElement.textContent = currentBid;
            updateHighestBidder("匿名竞标者", "red-text");
            resultMessageElement.textContent = "匿名竞标者已出价";
            updateBidHistory(currentBid, "匿名竞标者");
            updateBuyNowButton_formal();
            if (!auctionStarted) {
              auctionStarted = true;
              startAuction();
            } else {
              timeLeft = 30;
            }
          }, botReactionDelay[Math.floor(Math.random() * botReactionDelay.length)]);
        }
      }
      
      placeBidButton.addEventListener('click', () => {
        const userBid = parseInt(userBidElement.value);
        if (userBid > 500000) {
          resultMessageElement.textContent = "您的虚拟货币仅有500000 MU，请输入不超过500000 MU的出价。";
          return;
        }
        
        // ========== 若出价>=buyNowPrice_formal，立即成交 ==========
        if (userBid >= buyNowPrice_formal) {
          clearInterval(timer);
          currentBid = buyNowPrice_formal;
          currentBidElement.textContent = currentBid;
          updateHighestBidder("您", "green-text");
          resultMessageElement.textContent = `拍卖结束，恭喜您拍得此车辆的使用权！`;
          activityLog.immediatePurchase = true;
          activityLog.finalWinner = true;
          updateBidHistory(currentBid, "您（出价超立即购）");
          // 拍卖收益后续在 endAuction逻辑里不再走，因此我们手动收尾:
          userBidElement.disabled = true;
          placeBidButton.disabled = true;
          buyNowButton.disabled = true;
          
          // 同步更新结果区
          document.getElementById('finalResult').style.display = "block";
          document.getElementById('finalBid').textContent = currentBid;
          document.getElementById('realValue').textContent = fixedCarValueMU;
          
          // 修改点1：人类参与者成功拍得，隐藏虚拟收益和现金奖励显示
          document.getElementById('profitParagraph').style.display = "none";
          document.getElementById('cashParagraph').style.display = "none";
          
          nextButton.style.display = "block";
          return;
        }
        
        if (userBid >= currentBid + botMinIncrease) {
          currentBid = userBid;
          currentBidElement.textContent = currentBid;
          updateHighestBidder("您", "green-text");
          resultMessageElement.textContent = "您已成功出价！";
          updateBidHistory(currentBid, "您");
          updateBuyNowButton_formal();
          if (!auctionStarted) {
            auctionStarted = true;
            startAuction();
          } else {
            timeLeft = 30;
          }
          botBid();
        } else {
          resultMessageElement.textContent = '您的出价必须比当前价格高至少 5000 MU。';
        }
      });
      
      buyNowButton.addEventListener('click', () => {
        if(confirm("您是否确定以 300,000 MU 立即购买？")) {
          clearInterval(timer);
          currentBid = buyNowPrice_formal;
          currentBidElement.textContent = currentBid;
          updateHighestBidder("您", "green-text");
          resultMessageElement.textContent = `拍卖结束，恭喜您拍得此车辆的使用权！`;
          activityLog.immediatePurchase = true;
          activityLog.finalWinner = true;
          updateBidHistory(buyNowPrice_formal, "您（立即购买）");
          
          userBidElement.disabled = true;
          placeBidButton.disabled = true;
          buyNowButton.disabled = true;
          
          // 同步更新结果区
          finalResultDiv.style.display = "block";
          finalBidElement.textContent = currentBid;
          realValueElement.textContent = fixedCarValueMU;
          
          // 修改点1：人类参与者成功拍得，隐藏虚拟收益和现金奖励显示
          document.getElementById('profitParagraph').style.display = "none";
          document.getElementById('cashParagraph').style.display = "none";
          
          nextButton.style.display = "block";
        }
      });
      
      nextButton.addEventListener('click', () => {
        showPage('page5');
      });
    })();
    
    /********** 问卷逻辑：5 个页面 **********/
    // page5
    document.getElementById("surveyPage1").addEventListener("submit", function(e){
      e.preventDefault();
      // 检查必选
      if (!document.querySelector('input[name="q1"]:checked') ||
          !document.querySelector('input[name="q2"]:checked') ||
          !document.querySelector('input[name="q3"]:checked')) {
        document.getElementById("surveyPage1Error").textContent = "请回答所有必答题目。";
        return;
      }
      // 保存数据
      let formData = new FormData(e.target);
      formData.forEach((value, key) => {
        activityLog.surveyResponses[key] = value;
      });
      showPage('page6');
    });
    
    // page6
    document.getElementById("surveyPage2").addEventListener("submit", function(e){
      e.preventDefault();
      for (let i=4; i<=9; i++){
        let qName = "q"+i;
        if (!document.querySelector(`input[name="${qName}"]:checked`)) {
          document.getElementById("surveyPage2Error").textContent = "请回答所有必答题目。";
          return;
        }
      }
      let formData = new FormData(e.target);
      formData.forEach((value, key) => {
        activityLog.surveyResponses[key] = value;
      });
      showPage('page7');
    });
    
    // page7
    document.getElementById("surveyPage3").addEventListener("submit", function(e){
      e.preventDefault();
      for (let i=10; i<=14; i++){
        let qName = "q"+i;
        if (!document.querySelector(`input[name="${qName}"]:checked`)) {
          document.getElementById("surveyPage3Error").textContent = "请回答所有必答题目。";
          return;
        }
      }
      let formData = new FormData(e.target);
      formData.forEach((value, key) => {
        activityLog.surveyResponses[key] = value;
      });
      showPage('page8');
    });
    
    // page8
    document.getElementById("surveyPage4").addEventListener("submit", function(e){
      e.preventDefault();
      for (let i=15; i<=17; i++){
        let qName = "q"+i;
        if (!document.querySelector(`input[name="${qName}"]:checked`)) {
          document.getElementById("surveyPage4Error").textContent = "请回答所有必答题目。";
          return;
        }
      }
      let formData = new FormData(e.target);
      formData.forEach((value, key) => {
        activityLog.surveyResponses[key] = value;
      });
      showPage('page9');
    });
    
    // page9
    document.getElementById("surveyPage5").addEventListener("submit", function(e){
      e.preventDefault();
      if (!document.querySelector('input[name="q18"]:checked') ||
          !document.querySelector('input[name="q19"]:checked') ||
          !document.querySelector('input[name="q20"]:checked') ||
          !document.querySelector('select[name="q21"]').value) {
        document.getElementById("surveyPage5Error").textContent = "请回答所有必答题目。";
        return;
      }
      let formData = new FormData(e.target);
      formData.forEach((value, key) => {
        activityLog.surveyResponses[key] = value;
      });
      showPage('page10');
    });
    
    /********** 页面10：风险偏好彩票测试与收益汇总 **********/
    (function(){
      const riskTestData = [
        { choice: 1, A: {desc:"90% 机会赢得10元，10% 机会赢得8元", prob:0.9, high:10, low:8},  B: {desc:"90% 机会赢得20元，10% 机会赢得2元", prob:0.9, high:20, low:2} },
        { choice: 2, A: {desc:"80% 机会赢得10元，20% 机会赢得8元", prob:0.8, high:10, low:8},  B: {desc:"80% 机会赢得20元，20% 机会赢得2元", prob:0.8, high:20, low:2} },
        { choice: 3, A: {desc:"70% 机会赢得10元，30% 机会赢得8元", prob:0.7, high:10, low:8},  B: {desc:"70% 机会赢得20元，30% 机会赢得2元", prob:0.7, high:20, low:2} },
        { choice: 4, A: {desc:"60% 机会赢得10元，40% 机会赢得8元", prob:0.6, high:10, low:8},  B: {desc:"60% 机会赢得20元，40% 机会赢得2元", prob:0.6, high:20, low:2} },
        { choice: 5, A: {desc:"50% 机会赢得10元，50% 机会赢得8元", prob:0.5, high:10, low:8},  B: {desc:"50% 机会赢得20元，50% 机会赢得2元", prob:0.5, high:20, low:2} },
        { choice: 6, A: {desc:"40% 机会赢得10元，60% 机会赢得8元", prob:0.4, high:10, low:8},  B: {desc:"40% 机会赢得20元，60% 机会赢得2元", prob:0.4, high:20, low:2} },
        { choice: 7, A: {desc:"30% 机会赢得10元，70% 机会赢得8元", prob:0.3, high:10, low:8},  B: {desc:"30% 机会赢得20元，70% 机会赢得2元", prob:0.3, high:20, low:2} },
        { choice: 8, A: {desc:"20% 机会赢得10元，80% 机会赢得8元", prob:0.2, high:10, low:8},  B: {desc:"20% 机会赢得20元，80% 机会赢得2元", prob:0.2, high:20, low:2} },
        { choice: 9, A: {desc:"10% 机会赢得10元，90% 机会赢得8元", prob:0.1, high:10, low:8},  B: {desc:"10% 机会赢得20元，90% 机会赢得2元", prob:0.1, high:20, low:2} },
        { choice: 10,A: {desc:"100% 机会赢得9元",    prob:1.0, high:9, low:9},    B: {desc:"100% 机会赢得9元",    prob:1.0, high:9, low:9} }
      ];
      let currentRiskIndex = 0;
      let riskResponses = [];
      const riskQuestionElement = document.getElementById("riskQuestion");
      const riskOptionsElement = document.getElementById("riskOptions");
      const riskProgressElement = document.getElementById("riskProgress");
      const nextRiskButton = document.getElementById("nextRiskButton");
      
      function loadRiskQuestion(index) {
        const data = riskTestData[index];
        riskQuestionElement.textContent = "Choice #" + data.choice;
        riskOptionsElement.innerHTML = "";
        const labelA = document.createElement("label");
        labelA.innerHTML = `<input type="radio" name="riskOption" value="A" required> A: ${data.A.desc}`;
        const labelB = document.createElement("label");
        labelB.innerHTML = `<input type="radio" name="riskOption" value="B" required> B: ${data.B.desc}`;
        riskOptionsElement.appendChild(labelA);
        riskOptionsElement.appendChild(labelB);
        riskProgressElement.textContent = (index + 1) + "/10";
        nextRiskButton.disabled = true;
      }
      
      riskOptionsElement.addEventListener("change", function(){
        nextRiskButton.disabled = false;
      });
      
      nextRiskButton.addEventListener("click", function(){
        const selected = document.querySelector('input[name="riskOption"]:checked');
        if(selected){
          riskResponses[currentRiskIndex] = selected.value;
          currentRiskIndex++;
          if(currentRiskIndex < riskTestData.length){
            loadRiskQuestion(currentRiskIndex);
          } else {
            activityLog.riskResponses = riskResponses;
            let randomIndex = Math.floor(Math.random() * riskTestData.length);
            let chosenOption = riskResponses[randomIndex];
            let optionData = riskTestData[randomIndex][chosenOption];
            let randNum = Math.random();
            let bonus = (randNum < optionData.prob) ? optionData.high : optionData.low;
            activityLog.lotteryBonus = bonus;
            document.getElementById("lotteryResult").textContent = `根据抽奖结果，您获得的奖金为 ${bonus} 元。`;
            
            // 显示收益汇总和支付宝输入区域
            document.getElementById("finalPaymentArea").style.display = "block";
            
            // 计算并显示总收益信息
            let totalPayment = 0;
            if (activityLog.finalWinner) {
              // 成功拍得
              totalPayment = activityLog.lotteryBonus + 50;
              document.getElementById("finalMessage").innerHTML = `
                您的拍卖结果：已成功拍得车辆使用权。<br>
                由于该车辆为概念车，不具备驾驶条件，我们将为您提供 50 元人民币补偿。<br>
                此外，您的彩票奖金为 ${activityLog.lotteryBonus} 元。<br>
                因此，您的总收益为：<strong>${totalPayment} 元</strong>。
              `;
            } else {
              // 未拍得 或 拍得但低于保留价 -> 无效
              // 计算拍卖收益：如果达到保留价则有收益，否则为0
              let auctionCashReward = 0;
              if (activityLog.auctionProfit !== 0) {
                auctionCashReward = (activityLog.auctionProfit / 10000 * 5);
              }
              
              totalPayment = activityLog.lotteryBonus + auctionCashReward;
              
              if (activityLog.auctionProfit === 0) {
                document.getElementById("finalMessage").innerHTML = `
                  您未能有效拍得该车辆，或成交价低于保留价而导致无效。<br>
                  您的拍卖收益为 0。<br>
                  您的彩票奖金为 ${activityLog.lotteryBonus} 元。<br>
                  因此，您的总收益为：<strong>${totalPayment.toFixed(2)} 元</strong>。
                `;
              } else {
                document.getElementById("finalMessage").innerHTML = `
                  您未能拍得该车辆，但由于成交价高于保留价，您仍有拍卖收益。<br>
                  您的拍卖收益为 ${auctionCashReward.toFixed(2)} 元。<br>
                  您的彩票奖金为 ${activityLog.lotteryBonus} 元。<br>
                  因此，您的总收益为：<strong>${totalPayment.toFixed(2)} 元</strong>。
                `;
              }
            }
          }
        }
      });
      
      // 支付宝账号提交和确认逻辑
      document.getElementById("submitAlipay").addEventListener("click", function(){
        const alipay = document.getElementById("alipayAccount").value.trim();
        if(alipay === ""){
          alert("支付宝账号不能为空，请输入您的支付宝账号。");
          return;
        }
        
        // 显示确认区域
        document.getElementById("displayAlipay").textContent = alipay;
        document.getElementById("alipayInputArea").style.display = "none";
        document.getElementById("alipayConfirmArea").style.display = "block";
      });
      
      // 确认支付宝账号正确
      document.getElementById("confirmAlipay").addEventListener("click", function(){
        const alipay = document.getElementById("displayAlipay").textContent;
        activityLog.alipay = alipay;
        
        // 计算总收益用于显示
        let totalPayment = 0;
        if (activityLog.finalWinner) {
          totalPayment = activityLog.lotteryBonus + 50;
        } else {
          let auctionCashReward = 0;
          if (activityLog.auctionProfit !== 0) {
            auctionCashReward = (activityLog.auctionProfit / 10000 * 5);
          }
          totalPayment = activityLog.lotteryBonus + auctionCashReward;
        }
        
        // 显示最终感谢页面
        document.getElementById("alipayConfirmArea").style.display = "none";
        document.getElementById("finalThankYou").style.display = "block";
        document.getElementById("finalPaymentMsg").textContent = `您的总收益为 ${totalPayment.toFixed(2)} 元，将支付到您的支付宝账号：${alipay}`;
        
        console.log("完整活动日志：", activityLog);
      });
      
      // 重新编辑支付宝账号
      document.getElementById("editAlipay").addEventListener("click", function(){
        document.getElementById("alipayConfirmArea").style.display = "none";
        document.getElementById("alipayInputArea").style.display = "block";
      });
      
      loadRiskQuestion(0);
    })();
  </script>
</body>
</html>

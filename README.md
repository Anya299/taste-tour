<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Taste Tour – SIET Tumkur</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">
<style>
body {
  margin: 0;
  font-family: 'Orbitron', sans-serif;
  background: linear-gradient(135deg, #ffb3dd, #ffffff, #aee2ff);
  background-size: 400% 400%;
  animation: bgMove 15s infinite alternate;
  color: black;
  padding: 20px;
  text-align: center;
  position: relative;
  overflow-x: hidden;
}
@keyframes bgMove {0% {background-position: left;}100% {background-position: right;}}

/* HEADER */
h1 { font-size: 2.8rem; font-weight: bold; color: black; }
.subtext { font-size: 1.2rem; margin-top: -5px; margin-bottom: 20px; }

/* NAME POPUP */
#namePopup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 25px;
  border-radius: 15px;
  width: 300px;
  box-shadow: 0 0 20px #ff69b4;
  z-index: 1000;
}
#namePopup input { width: 90%; padding: 10px; margin-top: 10px; border: 2px solid #ff69b4; border-radius: 10px; font-weight: bold; }
#namePopup button { margin-top: 15px; padding: 10px 20px; border: none; background: #ff69b4; color: white; border-radius: 10px; cursor: pointer; font-weight:bold; }

/* CATEGORY BUTTONS */
.category-btn {
  padding: 20px 30px;
  margin: 10px;
  border: none;
  border-radius: 15px;
  font-size: 1.3rem;
  cursor: pointer;
  color: white;
  font-weight: bold;
  box-shadow: 0 0 10px #ff1493;
  transition: transform 0.3s;
}
.category-btn:hover { transform: scale(1.1); }
.category-btn.sweet {background: #ff69b4;}
.category-btn.spicy {background: #ff4500;}
.category-btn.healthy {background: #32cd32;}
.category-btn.bitter {background: #556b2f;}

/* MENU DISH BLOCKS */
.menu { display: flex; flex-wrap: wrap; justify-content: center; gap: 20px; margin-top: 20px; z-index:1; position:relative;}
.dish {
  background: white;
  width: 280px;
  padding: 15px;
  border-radius: 18px;
  border: 3px solid #ff69b4;
  box-shadow: 0 0 15px #ffb3dd;
  position: relative;
  text-align: left;
}
.dish h3 { color: #ff1493; margin-bottom: 10px; cursor: pointer; }
.dish small { display: block; margin-top: 5px; font-style: italic; color: black; }
.dish-details { display: none; margin-top: 10px; }
.dish-details ul { list-style: none; padding: 0; }

/* BUTTONS BELOW DISH */
.dish-btns { margin-top: 10px; display: flex; justify-content: space-between; gap:5px; }
.dish-btns button { padding: 8px 10px; border-radius: 8px; border: none; cursor: pointer; font-weight:bold; flex:1; transition: 0.2s; }
.info-btn { background:#ff1493; color:white; }
.qty-btn { background:#ffa500; color:white; }
.add-btn { background:#32cd32; color:white; }

/* ORDER REVIEW */
#orderReview {
  margin-top: 20px;
  padding: 15px;
  border: 2px dashed #ff1493;
  border-radius: 15px;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
  text-align: left;
}
.order-item { display: flex; justify-content: space-between; margin-bottom: 10px; }
.order-item button { background: red; color: white; border: none; padding: 5px 10px; border-radius: 8px; cursor: pointer; }

/* CONFIRM BUTTON */
#confirmBtn {
  margin-top: 20px;
  padding: 15px 30px;
  background: #ff69b4;
  color: white;
  border-radius: 15px;
  border: none;
  cursor: pointer;
  font-size: 1.3rem;
  box-shadow: 0 0 15px #ff1493;
}

/* STATUS POPUP */
#status {
  position: fixed;
  top: 40%;
  left: 50%;
  transform: translate(-50%,-50%);
  font-weight: bold;
  font-size: 1.5rem;
  color: #fff;
  background: #ff1493;
  padding: 15px 30px;
  border-radius: 15px;
  box-shadow: 0 0 20px #ff69b4;
  opacity: 0;
  z-index: 999;
  text-align: center;
  transition: all 0.3s ease-in-out;
}

/* CONFETTI */
.confetti { position: fixed; width: 10px; height: 10px; pointer-events:none; z-index:9999; font-size:18px; }

/* FLOWERS BACKGROUND */
.flower { position: absolute; font-size: 20px; pointer-events: none; animation: fall linear infinite; z-index:0; }
@keyframes fall {0% { transform: translateY(-10%); opacity: 0.9; }100% { transform: translateY(110vh); opacity: 0.2; }}

.team-members { margin-top: 30px; font-weight: bold; color: black; text-align:center; }
</style>
</head>
<body>

<!-- NAME POPUP -->
<div id="namePopup">
  <h3>Enter Your Name</h3>
  <input type="text" id="custName" placeholder="Your Name">
  <button onclick="saveName()">Done</button>
</div>

<h1>Taste Tour</h1>
<div class="subtext">
  Shridevi Institute of Engineering & Technology, Tumkur<br>
  Team: Taste of Life<br>
  Exploring the theme of life with dishes from different states of India
</div>

<!-- CATEGORY BUTTONS -->
<div>
  <button class="category-btn sweet" onclick="showCategory('sweet')">Sweet 🍬</button>
  <button class="category-btn spicy" onclick="showCategory('spicy')">Spicy 🌶️</button>
  <button class="category-btn healthy" onclick="showCategory('healthy')">Healthy 🥤</button>
  <button class="category-btn bitter" onclick="showCategory('bitter')">Bitter 🥒</button>
</div>

<div class="menu" id="menu"></div>

<div id="orderReview"><strong>Order Review:</strong></div>
<button id="confirmBtn" onclick="confirmOrder()">Confirm Order</button>
<div id="status"></div>
<div class="team-members">Team Members: Ananya • Yashaswini • Savita • Ramya • Ajay</div>

<script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
<script>
emailjs.init("eDkKaN76x5UK_XP2F");
let customerName = "";
let orderItems = [];

// DISH DATA
const dishesData = {
  sweet:[{name:"Fluffy Bread Dessert 🍞✨", place:"Karnataka 🌴", taste:"Sweet & Creamy", ingredients:["Sugar crystals","Golden food color","Milk powder","Fresh malai","Chopped almonds","Bread slices","Shredded coconut","Yellow cardamom powder","Cherry topping 🍒"], lifeTip:"Life’s layered sweetness in every bite! 💛", funBite:"Soft, fluffy, indulgent – like a cozy hug you can taste! 🤗"},{name:"Oreo Chocolate Dessert 🍫🍪", place:"Maharashtra 🌟", taste:"Sweet & Chocolaty", ingredients:["Creamy milk 🥛","Powdered sugar","Oreo cookies"], lifeTip:"Joyful surprises in every bite! 😋", funBite:"Crunchy, creamy, chocolaty – a mini celebration! 🎉"}],
  spicy:[{name:"Sweet Corn Pomegranate Salad 🌽🍎", place:"Karnataka 🌴", taste:"Tangy & Mildly Spicy", ingredients:["Pomegranate seeds","Sweet corn kernels","Shredded coconut 🥥","Fresh lemon 🍋","Pinch of salt & cracked black pepper"], lifeTip:"Life’s exciting twists in every bite! ⚡", funBite:"Sweet, tangy, a tiny adventure! 🎯"},{name:"Curd Rice 🍚🥛", place:"Tamil Nadu 🌟", taste:"Mild & Comforting", ingredients:["Fresh curd","Creamy milk","Tender rice","Tempering of spices (vagarane) 🌿"], lifeTip:"Comfort in hectic times – soothing and grounding! 🕊️", funBite:"Cool, creamy, subtly spiced – calming for the soul! ✨"},{name:"Mango Slices 🌶️🥭", place:"Maharashtra 🌟", taste:"Spicy & Tangy", ingredients:["Ripe mango slices 🥭","Sprinkle of salt & chili powder 🌶️"], lifeTip:"Bold, tangy adventures – embrace life’s zest! ⚡", funBite:"Sweet, tangy, spicy – a punch of excitement! 🎯"}],
  healthy:[{name:"Mojito 🍫🍋🌿", place:"Goa 🌴", taste:"Minty, Sweet & Fizzy", ingredients:["Pulsed chocolate","Zesty lemon 🍋","Fresh mint leaves 🌿","Pinch of salt","Fizzy soda 🥂","Sprinkle of chili & salt"], lifeTip:"Refresh yourself, recharge your energy! ⚡", funBite:"Sweet, tangy, minty – burst of freshness in every gulp! 🌟"},{name:"Pomegranate Mojito 🍎🌿", place:"Kerala 🌴", taste:"Tangy & Vibrant", ingredients:["Pomegranate seeds 🍎","Fresh mint 🌿","Zesty lemon 🍋","Sugar powder","Pinch of salt & chili powder"], lifeTip:"Stay vibrant, enjoy life’s zest! 💚", funBite:"Tangy, sweet, invigorating – a sip of vitality! ✨"}],
  bitter:[{name:"Bitter Gourd Juice 🥒🍋", place:"Rajasthan 🌟", taste:"Bitter & Zesty", ingredients:["Fresh bitter gourd","Zesty lemon 🍋","Ginger","Roasted jeera 🌿","Cracked black pepper","Pinch of salt"], lifeTip:"Challenges make you stronger! 💪", funBite:"Bitter, zesty, invigorating – a wake-up call for body & soul! ⚡"}]
};

// SAVE NAME
function saveName(){
  const nameInput = document.getElementById("custName").value.trim();
  if(nameInput===""){ alert("Please enter your name."); return; }
  customerName = nameInput;
  document.getElementById("namePopup").style.display="none";
}

// SHOW CATEGORY
function showCategory(cat){
  const menu = document.getElementById("menu");
  menu.innerHTML="";
  dishesData[cat].forEach((dish,i)=>{
    const dishDiv = document.createElement("div");
    dishDiv.className="dish";
    dishDiv.innerHTML = `
      <h3>${dish.name}</h3>
      <div><strong>From:</strong> ${dish.place} <br> <strong>Life Tip:</strong> ${dish.lifeTip}</div>
      <div class="dish-btns">
        <button class="info-btn" onclick="toggleDetails('${cat}',${i})">Info</button>
        <button class="qty-btn" onclick="changeQty('${cat}',${i},-1)">-</button>
        <span id="qty-${cat}-${i}" style="font-weight:bold; padding:5px 10px;">0</span>
        <button class="qty-btn" onclick="changeQty('${cat}',${i},1)">+</button>
        <button class="add-btn" onclick="addToOrder('${cat}',${i})">Add to Order</button>
      </div>
      <div class="dish-details" id="${cat}-${i}">
        <p><strong>Taste:</strong> ${dish.taste}</p>
        <p><strong>Ingredients:</strong></p>
        <ul>${dish.ingredients.map(ing=>`<li>${ing}</li>`).join("")}</ul>
        <p><strong>Fun Bite:</strong> ${dish.funBite}</p>
      </div>
    `;
    menu.appendChild(dishDiv);
  });
}

// TOGGLE DETAILS
function toggleDetails(cat,index){
  const details = document.getElementById(`${cat}-${index}`);
  details.style.display = (details.style.display==="none" || details.style.display==="") ? "block" : "none";
}

// CHANGE QUANTITY
function changeQty(cat,index,val){
  const span = document.getElementById(`qty-${cat}-${index}`);
  let qty = parseInt(span.innerText);
  qty += val;
  if(qty<0) qty=0;
  span.innerText = qty;
}

// ADD TO ORDER
function addToOrder(cat,index){
  const qty = parseInt(document.getElementById(`qty-${cat}-${index}`).innerText);
  if(qty<=0) return alert("Quantity must be at least 1");
  const dish = dishesData[cat][index];
  const existing = orderItems.find(item=>item.name===dish.name);
  if(existing){ existing.qty += qty; }
  else{ orderItems.push({name:dish.name, qty:qty}); }
  renderOrder();
}

// RENDER ORDER REVIEW
function renderOrder(){
  const review = document.getElementById("orderReview");
  review.innerHTML = "<strong>Order Review:</strong>";
  orderItems.forEach((item,i)=>{
    const div = document.createElement("div");
    div.className="order-item";
    div.innerHTML = `<span>${item.name} x ${item.qty}</span>
                     <button onclick="removeItem(${i})">Delete</button>`;
    review.appendChild(div);
  });
}

// REMOVE ITEM
function removeItem(index){
  orderItems.splice(index,1);
  renderOrder();
}

// CONFIRM ORDER
function confirmOrder(){
  if(orderItems.length===0){ alert("No items in order."); return; }
  if(!customerName){ alert("Please enter your name first!"); return; }

  const status = document.getElementById("status");
  const itemsList = orderItems.map(item => `• ${item.name} x ${item.qty}`).join('<br>');
  status.innerHTML = `🎉 <strong>${customerName}</strong>, your order has been sent to the team!<br>${itemsList}`;
  status.style.opacity = 1;
  status.style.transform = "translate(-50%, -50%) scale(1.2)";

  // Sparkle confetti effect
  const confettiContainer = document.createElement('div');
  confettiContainer.style.position='fixed';
  confettiContainer.style.top='50%';
  confettiContainer.style.left='50%';
  confettiContainer.style.width='100vw';
  confettiContainer.style.height='100vh';
  confettiContainer.style.pointerEvents='none';
  confettiContainer.style.zIndex='9999';
  document.body.appendChild(confettiContainer);
  const confettiEmojis = ['✨','💫','🌟','💖'];
  for(let i=0;i<80;i++){
    const conf = document.createElement('div');
    conf.className='confetti';
    conf.innerText = confettiEmojis[Math.floor(Math.random()*confettiEmojis.length)];
    conf.style.left = '50%';
    conf.style.top = '50%';
    conf.style.fontSize = (Math.random()*24+14)+'px';
    conf.style.opacity = 0.9;
    conf.style.transform=`translate(-50%, -50%) rotate(${Math.random()*360}deg)`;
    conf.style.transition='all 3s linear';
    confettiContainer.appendChild(conf);
    setTimeout(()=>{ conf.style.top=(Math.random()*100)+'vh'; conf.style.opacity=0; }, 50);
  }

  // --- SEND EMAIL ---
  const templateParams = {
      customer_name: customerName,
      team_order_number: Math.floor(Math.random()*10000),
      order_list: orderItems.map(item => `• ${item.name} x ${item.qty}`).join('\n')
  };
  emailjs.send('service_psgsmh3', 'template_qxih8fp', templateParams)
    .then(function(response) {
        console.log('SUCCESS!', response.status, response.text);
    }, function(error) {
        console.log('FAILED...', error);
    });

  setTimeout(()=>{
    status.style.opacity = 0;
    status.style.transform = "translate(-50%, -50%) scale(0.8)";
    confettiContainer.remove();
    orderItems=[];
    renderOrder();
    document.getElementById("namePopup").style.display="block";
    document.getElementById("custName").focus();
  },5000);
}

// FLOWERS BACKGROUND
const flowers=['🌸','🌺','💮'];
for(let i=0;i<40;i++){
  const f=document.createElement('div');
  f.className='flower';
  f.innerText=flowers[Math.floor(Math.random()*flowers.length)];
  f.style.left=Math.random()*100+'vw';
  f.style.top=Math.random()*-10+'vh';
  f.style.fontSize=(Math.random()*20+10)+'px';
  f.style.animationDuration=(Math.random()*20+10)+'s';
  document.body.appendChild(f);
}
</script>
</body>
</html>

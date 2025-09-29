# shopify-pre-order-button-messege-show

## Just Text Akare Pop Up Show korar Option

  Pre oder button show korar pore pop ba text show korar code

Liquid code


{%- if isPreoder -%}
  <div class="t4s-preorder-text-popup">
    <span class="t4s-close-popup">&times;</span>
    <b>Pre-order: </b> Please allow us 10-14 days to ship the item
  </div>
{%- endif -%}


Javascript Code

<script>
  document.addEventListener('DOMContentLoaded', function () {
    var preorderText = document.querySelector('.t4s-preorder-text-popup');
    var closeBtn = document.querySelector('.t4s-preorder-text-popup .t4s-close-popup');


    if (preorderText) {
      // টেক্সটটি fade-in effect সহ দেখানো
      setTimeout(function () {
        preorderText.classList.add('show');
      }, 500); // 0.5 সেকেন্ড delay


      // Close button ক্লিক করলে hide হবে
      if (closeBtn) {
        closeBtn.addEventListener('click', function () {
          preorderText.classList.remove('show');
        });
      }
    }
  });
</script>


Css

/* pre order */


.t4s-preorder-text-popup {
  position: relative; /* এখানে relative রাখা হলো যাতে parent div অনুযায়ী থাকে */
  background-color: rgba(255,255,255,0.95);
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 10px 15px;
  margin: 10px 0;
  width: 100%;
  text-align: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  opacity: 0;
  transform: translateY(-10px);
  transition: opacity 0.3s ease, transform 0.3s ease;
  z-index: 10;
}


.t4s-preorder-text-popup.show {
  opacity: 1;
  transform: translateY(0);
}


.t4s-preorder-text-popup .t4s-close-popup {
  position: absolute;
  top: 5px;
  right: 10px;
  cursor: pointer;
  font-size: 16px;
  color: #333;
}


## Style 2 Full page a Popup show

 ++ Product page er liquid Code 

     {%- if isPreoder -%}
  <div id="preorder-popup" class="t4s-preorder-popup">
    <div class="t4s-preorder-popup-content">
      <span class="t4s-close-popup">&times;</span>
      <b>Pre-order: </b> Please allow us 10-14 days to ship the item
    </div>
  </div>
{%- endif -%}

++ CSS code 

.t4s-preorder-popup {
  display: none; /* initially hidden */
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.5);
  z-index: 9999;
  justify-content: center;
  align-items: center;
}

.t4s-preorder-popup-content {
  background-color: #fff;
  padding: 20px 25px;
  border-radius: 10px;
  text-align: center;
  max-width: 400px;
  position: relative;
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

.t4s-preorder-popup-content b {
  font-size: 16px;
}

.t4s-close-popup {
  position: absolute;
  top: 10px;
  right: 15px;
  font-size: 20px;
  cursor: pointer;
}

++ Js Code 

document.addEventListener('DOMContentLoaded', function() {
  var popup = document.getElementById('preorder-popup');
  if(!popup) return; // যদি popup না থাকে, কিছু না করো

  var closeBtn = popup.querySelector('.t4s-close-popup');

  // Show popup automatically after 0.5s
  setTimeout(function() {
    popup.style.display = 'flex';
  }, 500);

  // Close button click
  closeBtn.addEventListener('click', function() {
    popup.style.display = 'none';
  });

  // Click outside content closes popup
  window.addEventListener('click', function(e) {
    if(e.target == popup) {
      popup.style.display = 'none';
    }
  });
});

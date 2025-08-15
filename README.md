<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>แบบฟอร์มเบิกอุปกรณ์</title>
  <style>
    :root{--bg:#f7f7fb;--card:#fff;--ink:#111;--muted:#666;--primary:#4f46e5;--bd:#e8e8ee}
    body{font-family:system-ui,Segoe UI,Roboto,Arial,sans-serif;background:var(--bg);margin:0;color:var(--ink)}
    .wrap{max-width:880px;margin:28px auto;padding:20px}
    .card{background:var(--card);border:1px solid var(--bd);border-radius:16px;box-shadow:0 8px 28px rgba(0,0,0,.06);padding:20px}
    h1{font-size:22px;margin:0 0 4px}
    .meta{color:var(--muted);margin-bottom:16px}
    .grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
    label{display:block;font-size:13px;margin:8px 0 6px}
    input,select,textarea{width:100%;padding:11px;border:1px solid var(--bd);border-radius:10px}
    textarea{resize:vertical}
    button{padding:11px 14px;border-radius:10px;border:0;cursor:pointer}
    .primary{background:var(--primary);color:#fff}
    .muted{background:#eef}
    table{width:100%;border-collapse:collapse;border:1px solid var(--bd);border-radius:12px;overflow:hidden}
    th,td{border-bottom:1px solid var(--bd);padding:8px 10px;font-size:14px}
    th{background:#f3f4f8;text-align:left}
    .actions{display:flex;gap:8px}
    .topbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
    .badge{font-size:12px;color:#444;background:#eef;border-radius:8px;padding:4px 8px;text-decoration:none}

    /* Success Popup */
    .overlay{position:fixed;inset:0;background:rgba(0,0,0,.5);display:none;align-items:center;justify-content:center;z-index:999}
    .overlay.show{display:flex}
    .modal{background:#fff;border-radius:18px;max-width:420px;width:92%;padding:24px;text-align:center;box-shadow:0 20px 60px rgba(0,0,0,.25)}
    .check{width:88px;height:88px;border-radius:50%;border:4px solid #22c55e;margin:0 auto 12px;position:relative}
    .check::after{content:"";position:absolute;left:22px;top:36px;width:24px;height:12px;border-left:6px solid #22c55e;border-bottom:6px solid #22c55e;transform:rotate(-45deg)}
    .confetti{position:absolute;inset:0;overflow:hidden;pointer-events:none}
    .confetti i{position:absolute;top:-10px;width:8px;height:16px;background:hsl(calc(var(--i)*36),90%,60%);animation:fall 1.8s linear infinite;opacity:.9}
    @keyframes fall{to{transform:translateY(120vh) rotate(360deg)}}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="topbar">
      <div>
        <h1>แบบฟอร์มเบิกอุปกรณ์</h1>
        <div class="meta">ผู้ใช้: <?!= userEmail || 'ไม่ทราบ (ต้องตั้งค่า Execute as: Me)' ?></div>
      </div>
      <div>
        <? if (isAdmin) { ?>
          <a class="badge" href="?page=admin">ไปหน้า Admin</a>
        <? } ?>
      </div>
    </div>

    <div class="card">
      <div class="grid">
        <div>
          <label>ชื่อ-สกุล</label>
          <input id="name" placeholder="กรอกชื่อผู้เบิก" required/>
        </div>
        <div>
          <label>รหัสพนักงาน</label>
          <input id="empId" placeholder="เช่น 012345"/>
        </div>
        <div>
          <label>แผนก/หน่วยงาน</label>
          <select id="dept">
            <option>ฝ่ายบริหาร</option>
            <option>ฝ่าย HR</option>
            <option>ฝ่าย IT</option>
            <option>ฝ่าย CS</option>
            <option>ฝ่าย Account</option>
            <option>ฝ่าย Cosmetic</option>
            <option>ฝ่าย ผลิตภัณฑ์กระติก</option>
            <option>ฝ่าย คลังสินค้า</option>
            <option>ฝ่าย จัดซื้อ</option>
            <option>ฝ่าย วางแผนการผลิต</option>
            <option>ฝ่าย วิศวกรรม</option>
            <option>ฝ่าย ตรวจสอบคุณภาพ</option>
            <option>ฝ่าย วิจัยและพัฒนา</option>
          </select>
        </div>
        <div>
          <label>ความเร่งด่วน</label>
          <select id="urgency">
            <option>ปกติ</option>
            <option>เร่งด่วน</option>
            <option>ด่วนมาก</option>
          </select>
        </div>
      </div>

      <div class="grid" style="margin-top:8px">
        <div>
          <label>วัตถุประสงค์ในการเบิก</label>
          <input id="purpose" placeholder="เช่น ใช้สำหรับงานเอกสารทั่วไป"/>
        </div>
        <div>
          <label>หมายเหตุ</label>
          <input id="notes" placeholder="ระบุข้อมูลเพิ่มเติม (ถ้ามี)"/>
        </div>
      </div>

      <label style="margin-top:12px;display:block">รายการขอเบิก</label>
      <table id="itemsTbl">
        <thead>
          <tr>
            <th style="width:50%">รายการ</th>
            <th style="width:20%">จำนวน</th>
            <th style="width:20%">หน่วย</th>
            <th style="width:10%">ลบ</th>
          </tr>
        </thead>
        <tbody></tbody>
      </table>
      <div class="actions" style="margin-top:8px">
        <button class="muted" onclick="addRow()" type="button">+ เพิ่มรายการ</button>
      </div>

      <div style="margin-top:14px">
        <button class="primary" onclick="submitForm()">ส่งคำขอ</button>
      </div>
    </div>
  </div>

  <!-- Success Popup -->
  <div class="overlay" id="ok">
    <div class="confetti" id="fx"></div>
    <div class="modal">
      <div class="check"></div>
      <h3>ส่งคำขอสำเร็จ</h3>
      <p id="reqid" style="color:#555;margin:6px 0 0">กำลังสร้างหมายเลขคำขอ…</p>
      <div style="margin-top:12px"><button onclick="hideOK()">ปิด</button></div>
    </div>
  </div>

  <script>
    function rowTpl(){
      const opts = ['ปากกาลูกลื่น','ดินสอ','สมุดโน้ต','ไฮไลท์','คลิปหนีบกระดาษ','แฟ้มเอกสาร','กระดาษ A4','กาวน้ำ','คัตเตอร์'];
      const sel = `<select class="item-name">${opts.map(o=>`<option>${o}</option>`).join('')}</select>`;
      return `<tr>\n<td>${sel}<input class="item-free" placeholder="หรือพิมพ์ชื่อเอง" style="margin-top:6px;width:100%;padding:8px;border:1px solid #e8e8ee;border-radius:8px"></td>\n<td><input class="item-qty" type="number" min="1" value="1"></td>\n<td><input class="item-unit" placeholder="ด้าม / กล่อง / รีม"></td>\n<td><button type="button" onclick="this.closest('tr').remove()">ลบ</button></td>\n</tr>`;
    }
    function addRow(){ document.querySelector('#itemsTbl tbody').insertAdjacentHTML('beforeend', rowTpl()); }
    addRow();

    function showOK(id){
      document.getElementById('reqid').textContent = `หมายเลขคำขอ: ${id}`;
      const ov = document.getElementById('ok');
      ov.classList.add('show');
      // สุ่ม confetti 20 ชิ้น
      const fx = document.getElementById('fx'); fx.innerHTML='';
      for(let i=0;i<20;i++){ const e=document.createElement('i'); e.style.left=Math.random()*100+'%'; e.style.setProperty('--i', i); fx.appendChild(e); }
    }
    function hideOK(){ document.getElementById('ok').classList.remove('show'); }

    function submitForm(){
      const name = document.getElementById('name').value.trim();
      const empId = document.getElementById('empId').value.trim();
      const dept = document.getElementById('dept').value;
      const purpose = document.getElementById('purpose').value.trim();
      const urgency = document.getElementById('urgency').value;
      const notes = document.getElementById('notes').value.trim();

      const rows = [...document.querySelectorAll('#itemsTbl tbody tr')];
      const items = rows.map(r=>({
        name: r.querySelector('.item-free').value.trim() || r.querySelector('.item-name').value,
        qty: Number(r.querySelector('.item-qty').value||1),
        unit: r.querySelector('.item-unit').value.trim()
      })).filter(x=>x.name);

      if(!name || items.length===0){
        alert('กรุณากรอกชื่อ และเพิ่มรายการอย่างน้อย 1 รายการ');
        return;
      }

      const payload = { name, empId, dept, purpose, urgency, items, notes };
      google.script.run.withSuccessHandler(function(res){
        if(res && res.ok){ showOK(res.id); clearForm(); }
      }).withFailureHandler(function(err){
        alert('บันทึกล้มเหลว: '+ (err && err.message ? err.message : err));
      }).submitRequest(payload);
    }

    function clearForm(){
      document.getElementById('name').value='';
      document.getElementById('empId').value='';
      document.getElementById('purpose').value='';
      document.getElementById('urgency').value='ปกติ';
      document.getElementById('notes').value='';
      document.querySelector('#itemsTbl tbody').innerHTML='';
      addRow();
    }
  </script>
</body>
</html>

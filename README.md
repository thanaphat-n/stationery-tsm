<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบเบิกอุปกรณ์สำนักงาน - Taisin</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap');
        body { font-family: 'Sarabun', sans-serif; }
        
        .fade-in {
            animation: fadeIn 0.5s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .slide-in {
            animation: slideIn 0.3s ease-out;
        }
        
        @keyframes slideIn {
            from { transform: translateX(-100%); }
            to { transform: translateX(0); }
        }
        
        .success-animation {
            animation: successPulse 0.6s ease-in-out;
        }
        
        @keyframes successPulse {
            0% { transform: scale(0.8); opacity: 0; }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); opacity: 1; }
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .card-shadow {
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        
        .hover-lift:hover {
            transform: translateY(-2px);
            transition: transform 0.2s ease;
        }
    </style>
</head>
<body class="bg-gray-50 min-h-screen">
    <!-- Header -->
    <header class="gradient-bg text-white shadow-lg">
        <div class="container mx-auto px-4 py-6">
            <div class="flex items-center justify-between">
                <div class="flex items-center space-x-3">
                    <i class="fas fa-clipboard-list text-3xl"></i>
                    <div>
                        <h1 class="text-2xl font-bold">ระบบเบิกอุปกรณ์สำนักงาน</h1>
                        <p class="text-2xl font-bold text-blue-100">บริษัท ไทยซิน แมนูแฟคเจอริ่ง จำกัด</p>
                    </div>
                </div>
                <div class="flex space-x-2">
                    <button onclick="showApproverLogin()" class="bg-white bg-opacity-20 hover:bg-opacity-30 px-4 py-2 rounded-lg transition-all">
                        <i class="fas fa-user-check mr-2"></i>ผู้อนุมัติ
                    </button>
                    <button onclick="showAdminLogin()" class="bg-white bg-opacity-20 hover:bg-opacity-30 px-4 py-2 rounded-lg transition-all">
                        <i class="fas fa-user-shield mr-2"></i>Admin
                    </button>
                    <button onclick="showReports()" class="bg-white bg-opacity-20 hover:bg-opacity-30 px-4 py-2 rounded-lg transition-all">
                        <i class="fas fa-chart-bar mr-2"></i>รายงาน
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <div class="container mx-auto px-4 py-8">
        <!-- Welcome Section -->
        <div id="welcomeSection" class="fade-in">
            <div class="bg-white rounded-xl card-shadow p-8 mb-8">
                <div class="text-center mb-8">
                    <i class="fas fa-info-circle text-4xl text-blue-500 mb-4"></i>
                    <h2 class="text-3xl font-bold text-gray-800 mb-4">ขั้นตอนการเบิกอุปกรณ์สำนักงาน</h2>
                </div>
                
                <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                    <div class="text-center p-6 bg-blue-50 rounded-lg hover-lift">
                        <div class="bg-blue-500 text-white w-12 h-12 rounded-full flex items-center justify-center mx-auto mb-4">
                            <span class="font-bold">1</span>
                        </div>
                        <h3 class="font-semibold text-gray-800 mb-2">กรอกข้อมูล</h3>
                        <p class="text-gray-600 text-sm">กรอกรายละเอียดการเบิกอุปกรณ์</p>
                    </div>
                    
                    <div class="text-center p-6 bg-green-50 rounded-lg hover-lift">
                        <div class="bg-green-500 text-white w-12 h-12 rounded-full flex items-center justify-center mx-auto mb-4">
                            <span class="font-bold">2</span>
                        </div>
                        <h3 class="font-semibold text-gray-800 mb-2">ส่งอีเมล</h3>
                        <p class="text-gray-600 text-sm">ส่งแจ้งเตือนไปยังผู้อนุมัติ</p>
                    </div>
                    
                    <div class="text-center p-6 bg-yellow-50 rounded-lg hover-lift">
                        <div class="bg-yellow-500 text-white w-12 h-12 rounded-full flex items-center justify-center mx-auto mb-4">
                            <span class="font-bold">3</span>
                        </div>
                        <h3 class="font-semibold text-gray-800 mb-2">รอการอนุมัติ</h3>
                        <p class="text-gray-600 text-sm">รอผู้มีอำนาจพิจารณาอนุมัติ</p>
                    </div>
                    
                    <div class="text-center p-6 bg-purple-50 rounded-lg hover-lift">
                        <div class="bg-purple-500 text-white w-12 h-12 rounded-full flex items-center justify-center mx-auto mb-4">
                            <span class="font-bold">4</span>
                        </div>
                        <h3 class="font-semibold text-gray-800 mb-2">อนุมัติ</h3>
                        <p class="text-gray-600 text-sm">ได้รับการอนุมัติและรับอุปกรณ์</p>
                    </div>
                </div>
                
                <div class="text-center">
                    <button onclick="showRequestForm()" class="bg-blue-600 hover:bg-blue-700 text-white px-8 py-3 rounded-lg font-semibold transition-all hover-lift">
                        <i class="fas fa-plus mr-2"></i>เริ่มทำรายการเบิก
                    </button>
                </div>
            </div>
        </div>

        <!-- Request Form -->
        <div id="requestForm" class="hidden fade-in">
            <div class="bg-white rounded-xl card-shadow p-8">
                <div class="flex items-center justify-between mb-6">
                    <h2 class="text-2xl font-bold text-gray-800">
                        <i class="fas fa-clipboard-list mr-2 text-blue-500"></i>ฟอร์มเบิกอุปกรณ์สำนักงาน
                    </h2>
                    <button onclick="showWelcome()" class="text-gray-500 hover:text-gray-700">
                        <i class="fas fa-times text-xl"></i>
                    </button>
                </div>

                <form id="supplyRequestForm" class="space-y-6">
                    <div class="grid md:grid-cols-2 gap-6">
                        <div>
                            <label class="block text-sm font-semibold text-gray-700 mb-2">ชื่อผู้เบิก *</label>
                            <input type="text" id="requesterName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                        </div>
                        
                        <div>
                            <label class="block text-sm font-semibold text-gray-700 mb-2">แผนก/หน่วยงาน *</label>
                            <select id="department" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                                <option value="">เลือกแผนก</option>
                                <option value="ฝ่ายบริหาร">ฝ่ายบริหาร</option>
                                <option value="ฝ่าย HR">ฝ่าย HR</option>
                                <option value="ฝ่าย IT">ฝ่าย IT</option>
                                <option value="ฝ่าย CS">ฝ่าย CS</option>
                                <option value="ฝ่าย Account">ฝ่าย Account</option>
                                <option value="ฝ่าย Cosmetic">ฝ่าย Cosmetic</option>
                                <option value="ฝ่าย ผลิตภัณฑ์กระติก">ฝ่าย ผลิตภัณฑ์กระติก</option>
                                <option value="ฝ่าย คลังสินค้า">ฝ่าย คลังสินค้า</option>
                                <option value="ฝ่าย จัดซื้อ">ฝ่าย จัดซื้อ</option>
                                <option value="ฝ่าย วางแผนการผลิต">ฝ่าย วางแผนการผลิต</option>
                                <option value="ฝ่าย วิศวกรรม">ฝ่าย วิศวกรรม</option>
                                <option value="ฝ่าย ตรวจสอบคุณภาพ">ฝ่าย ตรวจสอบคุณภาพ</option>
                                <option value="ฝ่าย วิจัยและพัฒนาผลิตภัณฑ์">ฝ่าย วิจัยและพัฒนาผลิตภัณฑ์</option>
                                <option value="ฝ่าย QMS/RA">ฝ่าย QMS/RA</option>
                                <option value="ฝ่าย ขาย">ฝ่าย ขาย</option>
                            </select>
                        </div>
                    </div>

                    <div class="grid md:grid-cols-2 gap-6">
                        <div>
                            <label class="block text-sm font-semibold text-gray-700 mb-2">วันที่ต้องการใช้</label>
                            <input type="date" id="requestDate" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                        </div>
                        
                        <div>
                            <label class="block text-sm font-semibold text-gray-700 mb-2">ผู้อนุมัติ</label>
                            <select id="approver" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                                <option value="">เลือกผู้อนุมัติ</option>
                                <option value="thanaphat.n@taisin.co.th">thanaphat.n@taisin.co.th</option>
                                <option value="jidapa.a@taisin.co.th">jidapa.a@taisin.co.th</option>
                                <option value="hatairat.k@taisin.co.th">hatairat.k@taisin.co.th</option>
                            </select>
                        </div>
                    </div>

                    <!-- Items Section -->
                    <div class="border-t pt-6">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-semibold text-gray-800">รายการอุปกรณ์ที่ต้องการเบิก</h3>
                            <button type="button" onclick="addItem()" class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg transition-all">
                                <i class="fas fa-plus mr-2"></i>เพิ่มรายการ
                            </button>
                        </div>
                        
                        <div id="itemsList" class="space-y-4">
                            <div class="item-row grid grid-cols-1 md:grid-cols-4 gap-4 p-4 bg-gray-50 rounded-lg">
                                <div>
                                    <label class="block text-sm font-medium text-gray-700 mb-1">รายการ</label>
                                    <select class="item-select w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                                        <option value="">เลือกรายการ</option>
                                        <option value="กระดาษ A4">กระดาษ A4</option>
                                        <option value="กระดาษ A3">กระดาษ A3</option>
                                        <option value="ปากกาลูกลื่นสีน้ำเงิน">ปากกาลูกลื่นสีน้ำเงิน</option>
                                        <option value="ปากกาลูกลื่นสีแดง">ปากกาลูกลื่นสีแดง</option>
                                        <option value="ปากกาไฮไลน์สีเหลือง">ปากกาไฮไลน์สีเหลือง</option>
                                        <option value="ปากกาไฮไลน์สีแดง">ปากกาไฮไลน์สีแดง</option>
                                        <option value="ปากกาไฮไลน์สีส้ม">ปากกาไฮไลน์สีส้ม</option>
                                        <option value="Max">Max</option>
                                        <option value="ลูกแม็กซ์">ลูกแม็กซ์</option>
                                        <option value="กรรไกร">กรรไกร</option>
                                        <option value="ซองถนอมเอกสาร 11 รู">ซองถนอมเอกสาร 11 รู</option>
                                        <option value="แฟ้ม 1 นิ้ว">แฟ้ม 1 นิ้ว</option>
                                        <option value="แฟ้ม 1.5 นิ้ว">แฟ้ม 1.5 นิ้ว</option>
                                        <option value="แฟ้ม 3 นิ้ว">แฟ้ม 3 นิ้ว</option>
                                        <option value="อื่นๆ">อื่นๆ (ระบุ)</option>
                                    </select>
                                </div>
                                
                                <div>
                                    <label class="block text-sm font-medium text-gray-700 mb-1">จำนวน</label>
                                    <input type="number" class="item-quantity w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" min="1">
                                </div>
                                
                                <div>
                                    <label class="block text-sm font-medium text-gray-700 mb-1">หน่วยนับ</label>
                                    <select class="item-unit w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                                        <option value="ชิ้น">ชิ้น</option>
                                        <option value="รีม">รีม</option>
                                        <option value="ด้าม">ด้าม</option>
                                        <option value="กล่อง">กล่อง</option>
                                        <option value="ตัว">ตัว</option>
                                        <option value="แพ็ค">แพ็ค</option>
                                        <option value="อัน">อัน</option>
                                    </select>
                                </div>
                                
                                <div class="flex items-end">
                                    <button type="button" onclick="removeItem(this)" class="bg-red-500 hover:bg-red-600 text-white px-3 py-2 rounded-lg transition-all">
                                        <i class="fas fa-trash"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-2">หมายเหตุ</label>
                        <textarea id="remarks" rows="3" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="ระบุรายละเอียดเพิ่มเติม (ถ้ามี)"></textarea>
                    </div>

                    <div class="flex flex-col sm:flex-row gap-4 pt-6">
                        <button type="submit" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white py-3 px-6 rounded-lg font-semibold transition-all hover-lift">
                            <i class="fas fa-paper-plane mr-2"></i>ส่งคำขอเบิก
                        </button>
                        <button type="button" onclick="exportToGoogleSheets()" class="flex-1 bg-green-600 hover:bg-green-700 text-white py-3 px-6 rounded-lg font-semibold transition-all hover-lift">
                            <i class="fas fa-table mr-2"></i>ส่งไป Google Sheets
                        </button>
                    </div>
                </form>
            </div>
        </div>

        <!-- Admin Panel -->
        <div id="adminPanel" class="hidden fade-in">
            <div class="bg-white rounded-xl card-shadow p-8">
                <div class="flex items-center justify-between mb-6">
                    <h2 class="text-2xl font-bold text-gray-800">
                        <i class="fas fa-user-shield mr-2 text-red-500"></i>ระบบจัดการ Admin
                    </h2>
                    <div class="flex space-x-2">
                        <button onclick="showWelcome()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg transition-all">
                            <i class="fas fa-arrow-left mr-2"></i>ย้อนกลับ
                        </button>
                        <button onclick="showWelcome()" class="text-gray-500 hover:text-gray-700">
                            <i class="fas fa-times text-xl"></i>
                        </button>
                    </div>
                </div>

                <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
                    <div class="bg-blue-50 p-6 rounded-lg text-center hover-lift">
                        <i class="fas fa-clipboard-list text-3xl text-blue-500 mb-4"></i>
                        <h3 class="font-semibold text-gray-800 mb-2">คำขอทั้งหมด</h3>
                        <p class="text-2xl font-bold text-blue-600" id="totalRequests">0</p>
                    </div>
                    
                    <div class="bg-yellow-50 p-6 rounded-lg text-center hover-lift">
                        <i class="fas fa-clock text-3xl text-yellow-500 mb-4"></i>
                        <h3 class="font-semibold text-gray-800 mb-2">รอการอนุมัติ</h3>
                        <p class="text-2xl font-bold text-yellow-600" id="pendingRequests">0</p>
                    </div>
                    
                    <div class="bg-green-50 p-6 rounded-lg text-center hover-lift">
                        <i class="fas fa-check-circle text-3xl text-green-500 mb-4"></i>
                        <h3 class="font-semibold text-gray-800 mb-2">อนุมัติแล้ว</h3>
                        <p class="text-2xl font-bold text-green-600" id="approvedRequests">0</p>
                    </div>
                    
                    <div class="bg-red-50 p-6 rounded-lg text-center hover-lift">
                        <i class="fas fa-times-circle text-3xl text-red-500 mb-4"></i>
                        <h3 class="font-semibold text-gray-800 mb-2">ไม่อนุมัติ</h3>
                        <p class="text-2xl font-bold text-red-600" id="rejectedRequests">0</p>
                    </div>
                </div>

                <div class="mt-8">
                    <div class="flex items-center justify-between mb-6">
                        <h3 class="text-lg font-semibold text-gray-800">จัดการผู้อนุมัติ</h3>
                        <button onclick="showAddApprover()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg transition-all">
                            <i class="fas fa-plus mr-2"></i>เพิ่มผู้อนุมัติ
                        </button>
                    </div>
                    
                    <div class="bg-gray-50 rounded-lg p-4 mb-8">
                        <div class="grid md:grid-cols-3 gap-4" id="approversList">
                            <div class="bg-white p-4 rounded-lg border flex items-center justify-between">
                                <div>
                                    <p class="font-semibold text-gray-800">thanaphat.n@taisin.co.th</p>
                                    <p class="text-sm text-gray-600">ผู้อนุมัติหลัก</p>
                                </div>
                                <div class="flex space-x-2">
                                    <button onclick="editApprover('thanaphat.n@taisin.co.th')" class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                    <button onclick="deleteApprover('thanaphat.n@taisin.co.th')" class="text-red-600 hover:text-red-800">
                                        <i class="fas fa-trash"></i>
                                    </button>
                                </div>
                            </div>
                            
                            <div class="bg-white p-4 rounded-lg border flex items-center justify-between">
                                <div>
                                    <p class="font-semibold text-gray-800">jidapa.a@taisin.co.th</p>
                                    <p class="text-sm text-gray-600">ผู้อนุมัติ</p>
                                </div>
                                <div class="flex space-x-2">
                                    <button onclick="editApprover('jidapa.a@taisin.co.th')" class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                    <button onclick="deleteApprover('jidapa.a@taisin.co.th')" class="text-red-600 hover:text-red-800">
                                        <i class="fas fa-trash"></i>
                                    </button>
                                </div>
                            </div>
                            
                            <div class="bg-white p-4 rounded-lg border flex items-center justify-between">
                                <div>
                                    <p class="font-semibold text-gray-800">hatairat.k@taisin.co.th</p>
                                    <p class="text-sm text-gray-600">ผู้อนุมัติ</p>
                                </div>
                                <div class="flex space-x-2">
                                    <button onclick="editApprover('hatairat.k@taisin.co.th')" class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                    <button onclick="deleteApprover('hatairat.k@taisin.co.th')" class="text-red-600 hover:text-red-800">
                                        <i class="fas fa-trash"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>

                <div class="mt-8">
                    <h3 class="text-lg font-semibold text-gray-800 mb-4">รายการคำขอล่าสุด</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full bg-white border border-gray-200 rounded-lg">
                            <thead class="bg-gray-50">
                                <tr>
                                    <th class="px-4 py-3 text-left text-sm font-semibold text-gray-700">วันที่</th>
                                    <th class="px-4 py-3 text-left text-sm font-semibold text-gray-700">ผู้เบิก</th>
                                    <th class="px-4 py-3 text-left text-sm font-semibold text-gray-700">แผนก</th>
                                    <th class="px-4 py-3 text-left text-sm font-semibold text-gray-700">สถานะ</th>
                                    <th class="px-4 py-3 text-left text-sm font-semibold text-gray-700">การจัดการ</th>
                                </tr>
                            </thead>
                            <tbody id="requestsTable">
                                <tr>
                                    <td colspan="5" class="px-4 py-8 text-center text-gray-500">ยังไม่มีข้อมูลคำขอ</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

        <!-- Approver Panel -->
        <div id="approverPanel" class="hidden fade-in">
            <div class="bg-white rounded-xl card-shadow p-8">
                <div class="flex items-center justify-between mb-6">
                    <h2 class="text-2xl font-bold text-gray-800">
                        <i class="fas fa-user-check mr-2 text-green-500"></i>ระบบอนุมัติคำขอ
                    </h2>
                    <div class="flex space-x-2">
                        <button onclick="showWelcome()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg transition-all">
                            <i class="fas fa-arrow-left mr-2"></i>ย้อนกลับ
                        </button>
                        <button onclick="showWelcome()" class="text-gray-500 hover:text-gray-700">
                            <i class="fas fa-times text-xl"></i>
                        </button>
                    </div>
                </div>

                <!-- Summary Cards for Approver -->
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="bg-yellow-50 p-6 rounded-lg text-center hover-lift">
                        <i class="fas fa-clock text-3xl text-yellow-500 mb-4"></i>
                        <h3 class="font-semibold text-gray-800 mb-2">รอการอนุมัติ</h3>
                        <p class="text-2xl font-bold text-yellow-600" id="approverPendingRequests">0</p>
                    </div>
                    
                    <div class="bg-green-50 p-6 rounded-lg text-center hover-lift">
                        <i class="fas fa-check-circle text-3xl text-green-500 mb-4"></i>
                        <h3 class="font-semibold text-gray-800 mb-2">อนุมัติแล้ว</h3>
                        <p class="text-2xl font-bold text-green-600" id="approverApprovedRequests">0</p>
                    </div>
                    
                    <div class="bg-red-50 p-6 rounded-lg text-center hover-lift">
                        <i class="fas fa-times-circle text-3xl text-red-500 mb-4"></i>
                        <h3 class="font-semibold text-gray-800 mb-2">ไม่อนุมัติ</h3>
                        <p class="text-2xl font-bold text-red-600" id="approverRejectedRequests">0</p>
                    </div>
                </div>

                <!-- Filter Section -->
                <div class="bg-gray-50 rounded-lg p-4 mb-6">
                    <div class="flex flex-wrap gap-4 items-center">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">กรองตามสถานะ</label>
                            <select id="statusFilter" onchange="filterApproverRequests()" class="px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                                <option value="">ทั้งหมด</option>
                                <option value="รอการอนุมัติ">รอการอนุมัติ</option>
                                <option value="อนุมัติ">อนุมัติแล้ว</option>
                                <option value="ไม่อนุมัติ">ไม่อนุมัติ</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">กรองตามแผนก</label>
                            <select id="departmentFilter" onchange="filterApproverRequests()" class="px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                                <option value="">ทั้งหมด</option>
                                <option value="ฝ่ายบริหาร">ฝ่ายบริหาร</option>
                                <option value="ฝ่าย HR">ฝ่าย HR</option>
                                <option value="ฝ่าย IT">ฝ่าย IT</option>
                                <option value="ฝ่าย CS">ฝ่าย CS</option>
                                <option value="ฝ่าย Account">ฝ่าย Account</option>
                                <option value="ฝ่าย Cosmetic">ฝ่าย Cosmetic</option>
                            </select>
                        </div>
                        <div class="flex-1"></div>
                        <button onclick="refreshApproverData()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg transition-all">
                            <i class="fas fa-sync-alt mr-2"></i>รีเฟรช
                        </button>
                    </div>
                </div>

                <!-- Requests Table for Approver -->
                <div class="bg-white rounded-lg border border-gray-200 overflow-hidden">
                    <div class="px-6 py-4 bg-gray-50 border-b border-gray-200">
                        <h3 class="text-lg font-semibold text-gray-800">คำขอที่ต้องพิจารณา</h3>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="w-full">
                            <thead class="bg-gray-50">
                                <tr>
                                    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-700">วันที่ส่งคำขอ</th>
                                    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-700">ผู้เบิก</th>
                                    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-700">แผนก</th>
                                    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-700">วันที่ต้องการใช้</th>
                                    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-700">จำนวนรายการ</th>
                                    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-700">สถานะ</th>
                                    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-700">การจัดการ</th>
                                </tr>
                            </thead>
                            <tbody id="approverRequestsTable">
                                <tr>
                                    <td colspan="7" class="px-6 py-8 text-center text-gray-500">ยังไม่มีข้อมูลคำขอ</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

        <!-- Reports Panel -->
        <div id="reportsPanel" class="hidden fade-in">
            <div class="bg-white rounded-xl card-shadow p-8">
                <div class="flex items-center justify-between mb-6">
                    <h2 class="text-2xl font-bold text-gray-800">
                        <i class="fas fa-chart-bar mr-2 text-green-500"></i>รายงานสถิติและกราฟ
                    </h2>
                    <div class="flex space-x-2">
                        <button onclick="exportReport()" class="bg-green-600 hover:bg-green-700 text-white px-4 py-2 rounded-lg transition-all">
                            <i class="fas fa-download mr-2"></i>ส่งออกรายงาน
                        </button>
                        <button onclick="refreshReports()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg transition-all">
                            <i class="fas fa-sync-alt mr-2"></i>รีเฟรช
                        </button>
                        <button onclick="showWelcome()" class="text-gray-500 hover:text-gray-700">
                            <i class="fas fa-times text-xl"></i>
                        </button>
                    </div>
                </div>

                <!-- Date Range Filter -->
                <div class="bg-gray-50 rounded-lg p-4 mb-6">
                    <div class="flex flex-wrap gap-4 items-center">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">ตั้งแต่วันที่</label>
                            <input type="date" id="reportStartDate" class="px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">ถึงวันที่</label>
                            <input type="date" id="reportEndDate" class="px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-1">แผนก</label>
                            <select id="reportDepartmentFilter" class="px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                                <option value="">ทุกแผนก</option>
                                <option value="ฝ่ายบริหาร">ฝ่ายบริหาร</option>
                                <option value="ฝ่าย HR">ฝ่าย HR</option>
                                <option value="ฝ่าย IT">ฝ่าย IT</option>
                                <option value="ฝ่าย CS">ฝ่าย CS</option>
                                <option value="ฝ่าย Account">ฝ่าย Account</option>
                                <option value="ฝ่าย Cosmetic">ฝ่าย Cosmetic</option>
                            </select>
                        </div>
                        <div class="flex items-end">
                            <button onclick="updateReportsData()" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg transition-all">
                                <i class="fas fa-filter mr-2"></i>กรองข้อมูล
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Summary Cards -->
                <div class="grid md:grid-cols-4 gap-6 mb-8">
                    <div class="bg-gradient-to-br from-blue-500 to-blue-600 p-6 rounded-xl text-white text-center hover-lift">
                        <i class="fas fa-clipboard-list text-4xl mb-3 opacity-80"></i>
                        <h3 class="font-semibold mb-2">คำขอทั้งหมด</h3>
                        <p class="text-3xl font-bold" id="reportTotalRequests">0</p>
                        <p class="text-sm opacity-80 mt-1">รายการ</p>
                    </div>
                    <div class="bg-gradient-to-br from-green-500 to-green-600 p-6 rounded-xl text-white text-center hover-lift">
                        <i class="fas fa-check-circle text-4xl mb-3 opacity-80"></i>
                        <h3 class="font-semibold mb-2">อนุมัติแล้ว</h3>
                        <p class="text-3xl font-bold" id="reportApprovedRequests">0</p>
                        <p class="text-sm opacity-80 mt-1" id="reportApprovalRate">0% ของทั้งหมด</p>
                    </div>
                    <div class="bg-gradient-to-br from-yellow-500 to-yellow-600 p-6 rounded-xl text-white text-center hover-lift">
                        <i class="fas fa-clock text-4xl mb-3 opacity-80"></i>
                        <h3 class="font-semibold mb-2">รอการอนุมัติ</h3>
                        <p class="text-3xl font-bold" id="reportPendingRequests">0</p>
                        <p class="text-sm opacity-80 mt-1">รายการ</p>
                    </div>
                    <div class="bg-gradient-to-br from-red-500 to-red-600 p-6 rounded-xl text-white text-center hover-lift">
                        <i class="fas fa-times-circle text-4xl mb-3 opacity-80"></i>
                        <h3 class="font-semibold mb-2">ไม่อนุมัติ</h3>
                        <p class="text-3xl font-bold" id="reportRejectedRequests">0</p>
                        <p class="text-sm opacity-80 mt-1" id="reportRejectionRate">0% ของทั้งหมด</p>
                    </div>
                </div>

                <!-- Charts Row 1 -->
                <div class="grid lg:grid-cols-2 gap-8 mb-8">
                    <!-- Department Chart -->
                    <div class="bg-white border border-gray-200 rounded-xl p-6 card-shadow">
                        <div class="flex items-center justify-between mb-6">
                            <h3 class="text-lg font-semibold text-gray-800">
                                <i class="fas fa-building mr-2 text-blue-500"></i>สถิติการเบิกตามแผนก
                            </h3>
                            <div class="text-sm text-gray-500">
                                <i class="fas fa-chart-bar mr-1"></i>แผนกที่เบิกมากที่สุด
                            </div>
                        </div>
                        <div id="departmentChart" class="space-y-4">
                            <!-- Chart will be populated by JavaScript -->
                        </div>
                    </div>

                    <!-- Status Pie Chart -->
                    <div class="bg-white border border-gray-200 rounded-xl p-6 card-shadow">
                        <div class="flex items-center justify-between mb-6">
                            <h3 class="text-lg font-semibold text-gray-800">
                                <i class="fas fa-chart-pie mr-2 text-green-500"></i>สัดส่วนสถานะคำขอ
                            </h3>
                            <div class="text-sm text-gray-500">
                                <i class="fas fa-percentage mr-1"></i>อัตราการอนุมัติ
                            </div>
                        </div>
                        <div class="flex items-center justify-center mb-6">
                            <div class="relative w-56 h-56">
                                <svg id="statusPieChart" class="w-full h-full transform -rotate-90" viewBox="0 0 100 100">
                                    <!-- Pie segments will be populated by JavaScript -->
                                </svg>
                                <div class="absolute inset-0 flex items-center justify-center">
                                    <div class="text-center">
                                        <div class="text-2xl font-bold text-gray-800" id="pieChartTotal">0</div>
                                        <div class="text-sm text-gray-600">รายการ</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div id="statusLegend" class="space-y-2">
                            <!-- Legend will be populated by JavaScript -->
                        </div>
                    </div>
                </div>

                <!-- Charts Row 2 -->
                <div class="grid lg:grid-cols-2 gap-8 mb-8">
                    <!-- Items Chart -->
                    <div class="bg-white border border-gray-200 rounded-xl p-6 card-shadow">
                        <div class="flex items-center justify-between mb-6">
                            <h3 class="text-lg font-semibold text-gray-800">
                                <i class="fas fa-box mr-2 text-purple-500"></i>อุปกรณ์ที่เบิกมากที่สุด
                            </h3>
                            <div class="text-sm text-gray-500">
                                <i class="fas fa-trophy mr-1"></i>Top 10 รายการ
                            </div>
                        </div>
                        <div id="itemsChart" class="space-y-3">
                            <!-- Chart will be populated by JavaScript -->
                        </div>
                    </div>

                    <!-- Monthly Trend Chart -->
                    <div class="bg-white border border-gray-200 rounded-xl p-6 card-shadow">
                        <div class="flex items-center justify-between mb-6">
                            <h3 class="text-lg font-semibold text-gray-800">
                                <i class="fas fa-chart-line mr-2 text-indigo-500"></i>แนวโน้มการเบิกรายเดือน
                            </h3>
                            <div class="text-sm text-gray-500">
                                <i class="fas fa-calendar-alt mr-1"></i>6 เดือนล่าสุด
                            </div>
                        </div>
                        <div class="flex items-end justify-between h-64 px-2" id="monthlyChart">
                            <!-- Chart will be populated by JavaScript -->
                        </div>
                    </div>
                </div>

                <!-- Detailed Statistics -->
                <div class="bg-white border border-gray-200 rounded-xl p-6 card-shadow">
                    <h3 class="text-lg font-semibold text-gray-800 mb-6">
                        <i class="fas fa-table mr-2 text-orange-500"></i>สถิติรายละเอียด
                    </h3>
                    
                    <div class="grid md:grid-cols-3 gap-6">
                        <!-- Top Requesters -->
                        <div>
                            <h4 class="font-semibold text-gray-700 mb-3 flex items-center">
                                <i class="fas fa-user-friends mr-2 text-blue-500"></i>ผู้เบิกมากที่สุด
                            </h4>
                            <div id="topRequesters" class="space-y-2">
                                <!-- Will be populated by JavaScript -->
                            </div>
                        </div>

                        <!-- Average Processing Time -->
                        <div>
                            <h4 class="font-semibold text-gray-700 mb-3 flex items-center">
                                <i class="fas fa-stopwatch mr-2 text-green-500"></i>เวลาเฉลี่ยในการอนุมัติ
                            </h4>
                            <div class="bg-gray-50 rounded-lg p-4">
                                <div class="text-2xl font-bold text-green-600" id="avgProcessingTime">-</div>
                                <div class="text-sm text-gray-600">วัน</div>
                                <div class="text-xs text-gray-500 mt-1">เฉลี่ยจากคำขอที่อนุมัติแล้ว</div>
                            </div>
                        </div>

                        <!-- Peak Hours -->
                        <div>
                            <h4 class="font-semibold text-gray-700 mb-3 flex items-center">
                                <i class="fas fa-clock mr-2 text-purple-500"></i>ช่วงเวลาที่เบิกมากที่สุด
                            </h4>
                            <div id="peakHours" class="space-y-2">
                                <!-- Will be populated by JavaScript -->
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Success Modal -->
    <div id="successModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
        <div class="bg-white rounded-xl p-8 max-w-md mx-4 text-center success-animation">
            <div class="mb-6">
                <div class="w-20 h-20 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-check text-3xl text-green-500"></i>
                </div>
                <h3 class="text-2xl font-bold text-gray-800 mb-2">ส่งคำขอสำเร็จ!</h3>
                <p class="text-gray-600">กรุณารอการอนุมัติจากผู้มีอำนาจ</p>
            </div>
            <button onclick="closeSuccessModal()" class="bg-green-500 hover:bg-green-600 text-white px-6 py-2 rounded-lg transition-all">
                ตกลง
            </button>
        </div>
    </div>

    <!-- Request Details Modal -->
    <div id="requestDetailsModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
        <div class="bg-white rounded-xl p-8 max-w-2xl mx-4 max-h-screen overflow-y-auto">
            <div class="flex items-center justify-between mb-6">
                <h3 class="text-xl font-bold text-gray-800">รายละเอียดคำขอเบิกอุปกรณ์</h3>
                <button onclick="closeRequestDetails()" class="text-gray-500 hover:text-gray-700">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div id="requestDetailsContent" class="space-y-4">
                <!-- Content will be populated by JavaScript -->
            </div>
            
            <div id="requestActions" class="flex space-x-4 mt-6 pt-6 border-t">
                <!-- Action buttons will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- Add/Edit Approver Modal -->
    <div id="approverModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
        <div class="bg-white rounded-xl p-8 max-w-md mx-4">
            <h3 class="text-xl font-bold text-gray-800 mb-4 text-center" id="approverModalTitle">เพิ่มผู้อนุมัติ</h3>
            <form id="approverForm">
                <div class="mb-4">
                    <label class="block text-sm font-semibold text-gray-700 mb-2">อีเมล</label>
                    <input type="email" id="approverEmail" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-semibold text-gray-700 mb-2">ตำแหน่ง</label>
                    <input type="text" id="approverPosition" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" placeholder="เช่น ผู้อนุมัติ, ผู้อนุมัติหลัก">
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-lg transition-all">บันทึก</button>
                    <button type="button" onclick="closeApproverModal()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-2 px-4 rounded-lg transition-all">ยกเลิก</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Approver Login Modal -->
    <div id="approverLoginModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
        <div class="bg-white rounded-xl p-8 max-w-md mx-4">
            <h3 class="text-xl font-bold text-gray-800 mb-4 text-center">เข้าสู่ระบบผู้อนุมัติ</h3>
            <form id="approverLoginForm">
                <div class="mb-4">
                    <label class="block text-sm font-semibold text-gray-700 mb-2">อีเมล</label>
                    <select id="approverLoginEmail" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" required>
                        <option value="">เลือกอีเมลผู้อนุมัติ</option>
                        <option value="thanaphat.n@taisin.co.th">thanaphat.n@taisin.co.th</option>
                        <option value="jidapa.a@taisin.co.th">jidapa.a@taisin.co.th</option>
                        <option value="hatairat.k@taisin.co.th">hatairat.k@taisin.co.th</option>
                    </select>
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-green-600 hover:bg-green-700 text-white py-2 px-4 rounded-lg transition-all">เข้าสู่ระบบ</button>
                    <button type="button" onclick="closeApproverLogin()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-2 px-4 rounded-lg transition-all">ยกเลิก</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Admin Login Modal -->
    <div id="adminLoginModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
        <div class="bg-white rounded-xl p-8 max-w-md mx-4">
            <h3 class="text-xl font-bold text-gray-800 mb-4 text-center">เข้าสู่ระบบ Admin</h3>
            <form id="adminLoginForm">
                <div class="mb-4">
                    <label class="block text-sm font-semibold text-gray-700 mb-2">รหัสผ่าน</label>
                    <input type="password" id="adminPassword" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-lg transition-all">เข้าสู่ระบบ</button>
                    <button type="button" onclick="closeAdminLogin()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-2 px-4 rounded-lg transition-all">ยกเลิก</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // Global variables
        let currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
        let approvers = JSON.parse(localStorage.getItem('approvers') || '[{"email":"thanaphat.n@taisin.co.th","position":"ผู้อนุมัติหลัก"},{"email":"jidapa.a@taisin.co.th","position":"ผู้อนุมัติ"},{"email":"hatairat.k@taisin.co.th","position":"ผู้อนุมัติ"}]');
        let editingApprover = null;
        let currentApproverEmail = null;
        
        // Function to create sample data
        function createSampleData() {
            const sampleRequests = [
                {
                    id: Date.now() - 86400000,
                    requesterName: 'สมชาย ใจดี',
                    department: 'ฝ่าย IT',
                    requestDate: '2024-01-15',
                    approver: 'thanaphat.n@taisin.co.th',
                    remarks: 'ใช้สำหรับงานประจำ',
                    items: [
                        { item: 'กระดาษ A4', quantity: 5, unit: 'รีม' },
                        { item: 'ปากกาลูกลื่นสีน้ำเงิน', quantity: 10, unit: 'ด้าม' }
                    ],
                    status: 'รอการอนุมัติ',
                    submittedAt: new Date(Date.now() - 86400000).toISOString()
                },
                {
                    id: Date.now() - 172800000,
                    requesterName: 'สมหญิง รักงาน',
                    department: 'ฝ่าย HR',
                    requestDate: '2024-01-16',
                    approver: 'jidapa.a@taisin.co.th',
                    remarks: 'เร่งด่วน',
                    items: [
                        { item: 'แฟ้ม 1 นิ้ว', quantity: 20, unit: 'อัน' },
                        { item: 'ซองถนอมเอกสาร 11 รู', quantity: 100, unit: 'ใบ' }
                    ],
                    status: 'รอการอนุมัติ',
                    submittedAt: new Date(Date.now() - 172800000).toISOString()
                },
                {
                    id: Date.now() - 259200000,
                    requesterName: 'สมศักดิ์ ขยัน',
                    department: 'ฝ่าย Account',
                    requestDate: '2024-01-17',
                    approver: 'hatairat.k@taisin.co.th',
                    remarks: '',
                    items: [
                        { item: 'ปากกาไฮไลน์สีเหลือง', quantity: 5, unit: 'ด้าม' },
                        { item: 'กรรไกร', quantity: 2, unit: 'อัน' }
                    ],
                    status: 'อนุมัติ',
                    submittedAt: new Date(Date.now() - 259200000).toISOString()
                },
                {
                    id: Date.now() - 345600000,
                    requesterName: 'สมใส ทำงาน',
                    department: 'ฝ่าย CS',
                    requestDate: '2024-01-18',
                    approver: 'hatairat.k@taisin.co.th',
                    remarks: 'ใช้สำหรับประชุมลูกค้า',
                    items: [
                        { item: 'กระดาษ A4', quantity: 2, unit: 'รีม' },
                        { item: 'ปากกาลูกลื่นสีน้ำเงิน', quantity: 5, unit: 'ด้าม' },
                        { item: 'แฟ้ม 1.5 นิ้ว', quantity: 3, unit: 'อัน' }
                    ],
                    status: 'รอการอนุมัติ',
                    submittedAt: new Date(Date.now() - 345600000).toISOString()
                },
                {
                    id: Date.now() - 432000000,
                    requesterName: 'สมปอง ขยัน',
                    department: 'ฝ่าย Cosmetic',
                    requestDate: '2024-01-19',
                    approver: 'jidapa.a@taisin.co.th',
                    remarks: 'สำหรับจัดทำเอกสารผลิตภัณฑ์ใหม่',
                    items: [
                        { item: 'ปากกาไฮไลน์สีเหลือง', quantity: 3, unit: 'ด้าม' },
                        { item: 'ปากกาไฮไลน์สีแดง', quantity: 2, unit: 'ด้าม' },
                        { item: 'ซองถนอมเอกสาร 11 รู', quantity: 50, unit: 'ใบ' }
                    ],
                    status: 'รอการอนุมัติ',
                    submittedAt: new Date(Date.now() - 432000000).toISOString()
                },
                {
                    id: Date.now() - 518400000,
                    requesterName: 'สมพร ดีใจ',
                    department: 'ฝ่าย จัดซื้อ',
                    requestDate: '2024-01-20',
                    approver: 'jidapa.a@taisin.co.th',
                    remarks: 'สำหรับจัดทำใบสั่งซื้อ',
                    items: [
                        { item: 'กระดาษ A4', quantity: 3, unit: 'รีม' },
                        { item: 'Max', quantity: 2, unit: 'ตัว' }
                    ],
                    status: 'รอการอนุมัติ',
                    submittedAt: new Date(Date.now() - 518400000).toISOString()
                },
                {
                    id: Date.now() - 604800000,
                    requesterName: 'สมหมาย ทำดี',
                    department: 'ฝ่าย คลังสินค้า',
                    requestDate: '2024-01-21',
                    approver: 'jidapa.a@taisin.co.th',
                    remarks: 'สำหรับติดป้ายสินค้า',
                    items: [
                        { item: 'ปากกาลูกลื่นสีแดง', quantity: 10, unit: 'ด้าม' },
                        { item: 'แฟ้ม 3 นิ้ว', quantity: 5, unit: 'อัน' }
                    ],
                    status: 'ไม่อนุมัติ',
                    submittedAt: new Date(Date.now() - 604800000).toISOString()
                }
            ];
            
            localStorage.setItem('officeSupplyRequests', JSON.stringify(sampleRequests));
            console.log('Sample data created:', sampleRequests.length, 'requests');
        }
        
        // Add sample data if no requests exist
        if (currentRequests.length === 0) {
            console.log('No existing requests found, creating sample data...');
            createSampleData();
            currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
        }
        
        // Approver mapping
        const approverMapping = {
            'ฝ่าย Account': 'hatairat.k@taisin.co.th',
            'ฝ่าย CS': 'hatairat.k@taisin.co.th',
            'ฝ่าย วางแผนการผลิต': 'jidapa.a@taisin.co.th',
            'ฝ่าย Cosmetic': 'jidapa.a@taisin.co.th',
            'ฝ่าย ผลิตภัณฑ์กระติก': 'jidapa.a@taisin.co.th',
            'ฝ่าย คลังสินค้า': 'jidapa.a@taisin.co.th',
            'ฝ่าย ตรวจสอบคุณภาพ': 'jidapa.a@taisin.co.th',
            'ฝ่าย วิจัยและพัฒนาผลิตภัณฑ์': 'jidapa.a@taisin.co.th',
            'ฝ่าย QMS/RA': 'jidapa.a@taisin.co.th',
            'ฝ่าย ขาย': 'jidapa.a@taisin.co.th',
            'ฝ่าย HR': 'thanaphat.n@taisin.co.th',
            'ฝ่าย วิศวกรรม': 'ruangchai.c@taisin.co.th'
        };

        // Navigation functions
        function showWelcome() {
            hideAllSections();
            document.getElementById('welcomeSection').classList.remove('hidden');
        }

        function showRequestForm() {
            hideAllSections();
            document.getElementById('requestForm').classList.remove('hidden');
        }

        function showAdminLogin() {
            document.getElementById('adminLoginModal').classList.remove('hidden');
            document.getElementById('adminLoginModal').classList.add('flex');
        }

        function closeAdminLogin() {
            document.getElementById('adminLoginModal').classList.add('hidden');
            document.getElementById('adminLoginModal').classList.remove('flex');
        }

        function showApproverLogin() {
            document.getElementById('approverLoginModal').classList.remove('hidden');
            document.getElementById('approverLoginModal').classList.add('flex');
        }

        function closeApproverLogin() {
            document.getElementById('approverLoginModal').classList.add('hidden');
            document.getElementById('approverLoginModal').classList.remove('flex');
        }

        function showReports() {
            hideAllSections();
            document.getElementById('reportsPanel').classList.remove('hidden');
            
            // Set default date range (last 30 days)
            const endDate = new Date();
            const startDate = new Date();
            startDate.setDate(startDate.getDate() - 30);
            
            document.getElementById('reportStartDate').value = startDate.toISOString().split('T')[0];
            document.getElementById('reportEndDate').value = endDate.toISOString().split('T')[0];
            
            // Load and update reports data
            updateReportsData();
        }

        function hideAllSections() {
            document.getElementById('welcomeSection').classList.add('hidden');
            document.getElementById('requestForm').classList.add('hidden');
            document.getElementById('adminPanel').classList.add('hidden');
            document.getElementById('approverPanel').classList.add('hidden');
            document.getElementById('reportsPanel').classList.add('hidden');
        }

        // Department change handler
        document.getElementById('department').addEventListener('change', function() {
            const department = this.value;
            const approverField = document.getElementById('approver');
            
            // Update approver dropdown with current approvers
            updateApproverDropdown();
            
            if (department && approverMapping[department]) {
                approverField.value = approverMapping[department];
            } else {
                approverField.value = '';
            }
        });

        function updateApproverDropdown() {
            const approverSelect = document.getElementById('approver');
            approverSelect.innerHTML = '<option value="">เลือกผู้อนุมัติ</option>';
            
            approvers.forEach(approver => {
                const option = document.createElement('option');
                option.value = approver.email;
                option.textContent = approver.email;
                approverSelect.appendChild(option);
            });
        }

        // Item management functions
        function addItem() {
            const itemsList = document.getElementById('itemsList');
            const newItem = document.createElement('div');
            newItem.className = 'item-row grid grid-cols-1 md:grid-cols-4 gap-4 p-4 bg-gray-50 rounded-lg slide-in';
            newItem.innerHTML = `
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">รายการ</label>
                    <select class="item-select w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                        <option value="">เลือกรายการ</option>
                        <option value="กระดาษ A4">กระดาษ A4</option>
                        <option value="กระดาษ A3">กระดาษ A3</option>
                        <option value="ปากกาลูกลื่นสีน้ำเงิน">ปากกาลูกลื่นสีน้ำเงิน</option>
                        <option value="ปากกาลูกลื่นสีแดง">ปากกาลูกลื่นสีแดง</option>
                        <option value="ปากกาไฮไลน์สีเหลือง">ปากกาไฮไลน์สีเหลือง</option>
                        <option value="ปากกาไฮไลน์สีแดง">ปากกาไฮไลน์สีแดง</option>
                        <option value="ปากกาไฮไลน์สีส้ม">ปากกาไฮไลน์สีส้ม</option>
                        <option value="Max">Max</option>
                        <option value="ลูกแม็กซ์">ลูกแม็กซ์</option>
                        <option value="กรรไกร">กรรไกร</option>
                        <option value="ซองถนอมเอกสาร 11 รู">ซองถนอมเอกสาร 11 รู</option>
                        <option value="แฟ้ม 1 นิ้ว">แฟ้ม 1 นิ้ว</option>
                        <option value="แฟ้ม 1.5 นิ้ว">แฟ้ม 1.5 นิ้ว</option>
                        <option value="แฟ้ม 3 นิ้ว">แฟ้ม 3 นิ้ว</option>
                        <option value="อื่นๆ">อื่นๆ (ระบุ)</option>
                    </select>
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">จำนวน</label>
                    <input type="number" class="item-quantity w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" min="1">
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">หน่วยนับ</label>
                    <select class="item-unit w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                        <option value="ชิ้น">ชิ้น</option>
                        <option value="รีม">รีม</option>
                        <option value="ด้าม">ด้าม</option>
                        <option value="กล่อง">กล่อง</option>
                        <option value="ตัว">ตัว</option>
                        <option value="แพ็ค">แพ็ค</option>
                        <option value="อัน">อัน</option>
                    </select>
                </div>
                
                <div class="flex items-end">
                    <button type="button" onclick="removeItem(this)" class="bg-red-500 hover:bg-red-600 text-white px-3 py-2 rounded-lg transition-all">
                        <i class="fas fa-trash"></i>
                    </button>
                </div>
            `;
            itemsList.appendChild(newItem);
        }

        function removeItem(button) {
            const itemRow = button.closest('.item-row');
            itemRow.remove();
        }

        // Form submission
        document.getElementById('supplyRequestForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = {
                id: Date.now(),
                requesterName: document.getElementById('requesterName').value,
                department: document.getElementById('department').value,
                requestDate: document.getElementById('requestDate').value,
                approver: document.getElementById('approver').value,
                remarks: document.getElementById('remarks').value,
                items: [],
                status: 'รอการอนุมัติ',
                submittedAt: new Date().toISOString()
            };

            // Collect items
            const itemRows = document.querySelectorAll('.item-row');
            itemRows.forEach(row => {
                const item = row.querySelector('.item-select').value;
                const quantity = row.querySelector('.item-quantity').value;
                const unit = row.querySelector('.item-unit').value;
                
                if (item && quantity) {
                    formData.items.push({
                        item: item,
                        quantity: parseInt(quantity),
                        unit: unit
                    });
                }
            });

            if (formData.items.length === 0) {
                alert('กรุณาเพิ่มรายการอุปกรณ์อย่างน้อย 1 รายการ');
                return;
            }

            // Save to localStorage
            currentRequests.push(formData);
            localStorage.setItem('officeSupplyRequests', JSON.stringify(currentRequests));

            // Send email
            sendEmailToApprover(formData);
            
            // Show success modal
            showSuccessModal();
            
            // Reset form
            this.reset();
            document.getElementById('approver').value = '';
        });

        function sendEmailToApprover(requestData) {
            const subject = `คำขอเบิกอุปกรณ์สำนักงาน - ${requestData.requesterName}`;
            const body = `
เรียน ผู้อนุมัติ

มีคำขอเบิกอุปกรณ์สำนักงานใหม่ รายละเอียดดังนี้:

ผู้เบิก: ${requestData.requesterName}
แผนก: ${requestData.department}
วันที่ต้องการใช้: ${requestData.requestDate}

รายการอุปกรณ์:
${requestData.items.map(item => `- ${item.item} จำนวน ${item.quantity} ${item.unit}`).join('\n')}

หมายเหตุ: ${requestData.remarks || 'ไม่มี'}

กรุณาพิจารณาอนุมัติ

ขอบคุณครับ/ค่ะ
            `;

            const mailtoLink = `mailto:${requestData.approver}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
            window.open(mailtoLink);
        }

        function showSuccessModal() {
            document.getElementById('successModal').classList.remove('hidden');
            document.getElementById('successModal').classList.add('flex');
        }

        function closeSuccessModal() {
            document.getElementById('successModal').classList.add('hidden');
            document.getElementById('successModal').classList.remove('flex');
            showWelcome();
        }

        // Approver login
        document.getElementById('approverLoginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('approverLoginEmail').value;
            
            if (email && approvers.find(a => a.email === email)) {
                currentApproverEmail = email;
                closeApproverLogin();
                hideAllSections();
                document.getElementById('approverPanel').classList.remove('hidden');
                updateApproverData();
            } else {
                alert('กรุณาเลือกอีเมลผู้อนุมัติ');
            }
        });

        // Admin login
        document.getElementById('adminLoginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const password = document.getElementById('adminPassword').value;
            
            if (password === '123456') {
                closeAdminLogin();
                hideAllSections();
                document.getElementById('adminPanel').classList.remove('hidden');
                updateAdminData();
            } else {
                alert('รหัสผ่านไม่ถูกต้อง');
            }
        });

        function updateAdminData() {
            const totalRequests = currentRequests.length;
            const pendingRequests = currentRequests.filter(r => r.status === 'รอการอนุมัติ').length;
            const approvedRequests = currentRequests.filter(r => r.status === 'อนุมัติ').length;
            const rejectedRequests = currentRequests.filter(r => r.status === 'ไม่อนุมัติ').length;

            document.getElementById('totalRequests').textContent = totalRequests;
            document.getElementById('pendingRequests').textContent = pendingRequests;
            document.getElementById('approvedRequests').textContent = approvedRequests;
            document.getElementById('rejectedRequests').textContent = rejectedRequests;

            // Update approvers list
            updateApproversList();

            // Update requests table
            const tableBody = document.getElementById('requestsTable');
            if (currentRequests.length === 0) {
                tableBody.innerHTML = '<tr><td colspan="5" class="px-4 py-8 text-center text-gray-500">ยังไม่มีข้อมูลคำขอ</td></tr>';
            } else {
                tableBody.innerHTML = currentRequests.slice(-10).reverse().map(request => `
                    <tr class="border-t">
                        <td class="px-4 py-3 text-sm text-gray-700">${new Date(request.submittedAt).toLocaleDateString('th-TH')}</td>
                        <td class="px-4 py-3 text-sm text-gray-700">${request.requesterName}</td>
                        <td class="px-4 py-3 text-sm text-gray-700">${request.department}</td>
                        <td class="px-4 py-3">
                            <span class="px-2 py-1 text-xs rounded-full ${getStatusColor(request.status)}">
                                ${request.status}
                            </span>
                        </td>
                        <td class="px-4 py-3">
                            <div class="flex space-x-2">
                                <button onclick="viewRequest(${request.id})" class="text-blue-600 hover:text-blue-800 text-sm">
                                    <i class="fas fa-eye mr-1"></i>ดู
                                </button>
                                ${request.status === 'รอการอนุมัติ' ? `
                                    <button onclick="adminApproveRequest(${request.id})" class="text-green-600 hover:text-green-800 text-sm font-medium px-2 py-1 rounded hover:bg-green-50">
                                        <i class="fas fa-check mr-1"></i>อนุมัติ
                                    </button>
                                    <button onclick="adminRejectRequest(${request.id})" class="text-red-600 hover:text-red-800 text-sm font-medium px-2 py-1 rounded hover:bg-red-50">
                                        <i class="fas fa-times mr-1"></i>ไม่อนุมัติ
                                    </button>
                                ` : ''}
                            </div>
                        </td>
                    </tr>
                `).join('');
            }
        }

        function getStatusColor(status) {
            switch(status) {
                case 'รอการอนุมัติ': return 'bg-yellow-100 text-yellow-800';
                case 'อนุมัติ': return 'bg-green-100 text-green-800';
                case 'ไม่อนุมัติ': return 'bg-red-100 text-red-800';
                default: return 'bg-gray-100 text-gray-800';
            }
        }

        function updateReportsData() {
            console.log('Updating reports data...');
            
            // Get filter values
            const startDate = document.getElementById('reportStartDate')?.value;
            const endDate = document.getElementById('reportEndDate')?.value;
            const departmentFilter = document.getElementById('reportDepartmentFilter')?.value;
            
            // Filter requests based on criteria
            let filteredRequests = [...currentRequests];
            
            if (startDate) {
                filteredRequests = filteredRequests.filter(r => 
                    new Date(r.submittedAt) >= new Date(startDate)
                );
            }
            
            if (endDate) {
                filteredRequests = filteredRequests.filter(r => 
                    new Date(r.submittedAt) <= new Date(endDate + 'T23:59:59')
                );
            }
            
            if (departmentFilter) {
                filteredRequests = filteredRequests.filter(r => 
                    r.department === departmentFilter
                );
            }
            
            // Update summary cards
            updateSummaryCards(filteredRequests);
            
            // Update charts
            updateDepartmentChart(filteredRequests);
            updateStatusPieChart(filteredRequests);
            updateItemsChart(filteredRequests);
            updateMonthlyChart(filteredRequests);
            updateDetailedStats(filteredRequests);
        }

        function updateSummaryCards(requests) {
            const total = requests.length;
            const approved = requests.filter(r => r.status === 'อนุมัติ').length;
            const pending = requests.filter(r => r.status === 'รอการอนุมัติ').length;
            const rejected = requests.filter(r => r.status === 'ไม่อนุมัติ').length;
            
            const approvalRate = total > 0 ? Math.round((approved / total) * 100) : 0;
            const rejectionRate = total > 0 ? Math.round((rejected / total) * 100) : 0;
            
            document.getElementById('reportTotalRequests').textContent = total;
            document.getElementById('reportApprovedRequests').textContent = approved;
            document.getElementById('reportPendingRequests').textContent = pending;
            document.getElementById('reportRejectedRequests').textContent = rejected;
            document.getElementById('reportApprovalRate').textContent = `${approvalRate}% ของทั้งหมด`;
            document.getElementById('reportRejectionRate').textContent = `${rejectionRate}% ของทั้งหมด`;
        }

        function updateDepartmentChart(requests) {
            const departmentStats = {};
            
            requests.forEach(request => {
                const dept = request.department;
                if (!departmentStats[dept]) {
                    departmentStats[dept] = 0;
                }
                departmentStats[dept]++;
            });
            
            const sortedDepts = Object.entries(departmentStats)
                .sort(([,a], [,b]) => b - a)
                .slice(0, 8);
            
            const maxCount = sortedDepts.length > 0 ? sortedDepts[0][1] : 1;
            const colors = ['#3B82F6', '#10B981', '#8B5CF6', '#F59E0B', '#EF4444', '#06B6D4', '#84CC16', '#F97316'];
            
            const chartHTML = sortedDepts.map(([dept, count], index) => {
                const percentage = Math.round((count / maxCount) * 100);
                const color = colors[index % colors.length];
                
                return `
                    <div class="flex items-center group hover:bg-gray-50 p-2 rounded-lg transition-all">
                        <div class="w-24 text-sm text-gray-700 font-medium">${dept.replace('ฝ่าย ', '')}</div>
                        <div class="flex-1 mx-3">
                            <div class="bg-gray-200 rounded-full h-8 relative overflow-hidden">
                                <div class="h-full rounded-full transition-all duration-1000 ease-out group-hover:opacity-80" 
                                     style="width: ${percentage}%; background-color: ${color}"></div>
                                <span class="absolute inset-0 flex items-center justify-center text-sm font-semibold text-white">
                                    ${count}
                                </span>
                            </div>
                        </div>
                        <div class="w-16 text-right text-sm font-semibold" style="color: ${color}">
                            ${Math.round((count / requests.length) * 100)}%
                        </div>
                    </div>
                `;
            }).join('');
            
            document.getElementById('departmentChart').innerHTML = chartHTML || 
                '<div class="text-center text-gray-500 py-8">ไม่มีข้อมูล</div>';
        }

        function updateStatusPieChart(requests) {
            const total = requests.length;
            if (total === 0) {
                document.getElementById('statusPieChart').innerHTML = '';
                document.getElementById('statusLegend').innerHTML = '<div class="text-center text-gray-500">ไม่มีข้อมูล</div>';
                document.getElementById('pieChartTotal').textContent = '0';
                return;
            }
            
            const approved = requests.filter(r => r.status === 'อนุมัติ').length;
            const pending = requests.filter(r => r.status === 'รอการอนุมัติ').length;
            const rejected = requests.filter(r => r.status === 'ไม่อนุมัติ').length;
            
            const segments = [
                { label: 'อนุมัติแล้ว', count: approved, color: '#10B981' },
                { label: 'รอการอนุมัติ', count: pending, color: '#F59E0B' },
                { label: 'ไม่อนุมัติ', count: rejected, color: '#EF4444' }
            ].filter(s => s.count > 0);
            
            let cumulativePercentage = 0;
            const circumference = 2 * Math.PI * 40; // radius = 40
            
            const svgContent = segments.map(segment => {
                const percentage = segment.count / total;
                const strokeDasharray = `${percentage * circumference} ${circumference}`;
                const strokeDashoffset = -cumulativePercentage * circumference;
                
                cumulativePercentage += percentage;
                
                return `
                    <circle cx="50" cy="50" r="40" fill="none" stroke="${segment.color}" stroke-width="20" 
                            stroke-dasharray="${strokeDasharray}" stroke-dashoffset="${strokeDashoffset}" 
                            class="transition-all duration-1000 hover:opacity-80">
                    </circle>
                `;
            }).join('');
            
            document.getElementById('statusPieChart').innerHTML = svgContent;
            document.getElementById('pieChartTotal').textContent = total;
            
            const legendHTML = segments.map(segment => `
                <div class="flex items-center justify-between p-2 rounded-lg hover:bg-gray-50">
                    <div class="flex items-center">
                        <div class="w-4 h-4 rounded mr-3" style="background-color: ${segment.color}"></div>
                        <span class="text-sm text-gray-700">${segment.label}</span>
                    </div>
                    <div class="text-right">
                        <span class="text-sm font-semibold text-gray-800">${segment.count}</span>
                        <span class="text-xs text-gray-500 ml-1">(${Math.round((segment.count/total)*100)}%)</span>
                    </div>
                </div>
            `).join('');
            
            document.getElementById('statusLegend').innerHTML = legendHTML;
        }

        function updateItemsChart(requests) {
            const itemStats = {};
            
            requests.forEach(request => {
                request.items.forEach(item => {
                    if (!itemStats[item.item]) {
                        itemStats[item.item] = 0;
                    }
                    itemStats[item.item] += item.quantity;
                });
            });
            
            const sortedItems = Object.entries(itemStats)
                .sort(([,a], [,b]) => b - a)
                .slice(0, 10);
            
            const maxCount = sortedItems.length > 0 ? sortedItems[0][1] : 1;
            const colors = ['#8B5CF6', '#06B6D4', '#10B981', '#F59E0B', '#EF4444', '#3B82F6', '#84CC16', '#F97316', '#EC4899', '#6366F1'];
            
            const chartHTML = sortedItems.map(([item, count], index) => {
                const percentage = Math.round((count / maxCount) * 100);
                const color = colors[index % colors.length];
                
                return `
                    <div class="flex items-center group hover:bg-gray-50 p-2 rounded-lg transition-all">
                        <div class="w-6 h-6 rounded-full mr-3 flex items-center justify-center text-white text-xs font-bold" 
                             style="background-color: ${color}">
                            ${index + 1}
                        </div>
                        <div class="flex-1">
                            <div class="text-sm font-medium text-gray-800 mb-1">${item}</div>
                            <div class="bg-gray-200 rounded-full h-4 relative overflow-hidden">
                                <div class="h-full rounded-full transition-all duration-1000 ease-out" 
                                     style="width: ${percentage}%; background-color: ${color}"></div>
                            </div>
                        </div>
                        <div class="ml-3 text-right">
                            <div class="text-sm font-bold" style="color: ${color}">${count}</div>
                            <div class="text-xs text-gray-500">ชิ้น</div>
                        </div>
                    </div>
                `;
            }).join('');
            
            document.getElementById('itemsChart').innerHTML = chartHTML || 
                '<div class="text-center text-gray-500 py-8">ไม่มีข้อมูล</div>';
        }

        function updateMonthlyChart(requests) {
            const monthlyStats = {};
            const months = ['ม.ค.', 'ก.พ.', 'มี.ค.', 'เม.ย.', 'พ.ค.', 'มิ.ย.', 'ก.ค.', 'ส.ค.', 'ก.ย.', 'ต.ค.', 'พ.ย.', 'ธ.ค.'];
            const colors = ['#3B82F6', '#10B981', '#8B5CF6', '#F59E0B', '#EF4444', '#06B6D4'];
            
            // Initialize last 6 months
            const now = new Date();
            for (let i = 5; i >= 0; i--) {
                const date = new Date(now.getFullYear(), now.getMonth() - i, 1);
                const key = `${date.getFullYear()}-${String(date.getMonth() + 1).padStart(2, '0')}`;
                monthlyStats[key] = {
                    count: 0,
                    label: months[date.getMonth()],
                    year: date.getFullYear()
                };
            }
            
            // Count requests by month
            requests.forEach(request => {
                const date = new Date(request.submittedAt);
                const key = `${date.getFullYear()}-${String(date.getMonth() + 1).padStart(2, '0')}`;
                if (monthlyStats[key]) {
                    monthlyStats[key].count++;
                }
            });
            
            const monthlyData = Object.values(monthlyStats);
            const maxCount = Math.max(...monthlyData.map(m => m.count), 1);
            
            const chartHTML = monthlyData.map((month, index) => {
                const height = Math.max((month.count / maxCount) * 200, 4);
                const color = colors[index % colors.length];
                
                return `
                    <div class="flex flex-col items-center group">
                        <div class="bg-gray-100 rounded-t w-12 mb-2 transition-all duration-1000 hover:opacity-80 relative overflow-hidden" 
                             style="height: ${height}px;">
                            <div class="absolute bottom-0 left-0 right-0 rounded-t transition-all duration-1000" 
                                 style="height: 100%; background-color: ${color}"></div>
                            <div class="absolute inset-0 flex items-center justify-center">
                                <span class="text-xs font-bold text-white opacity-0 group-hover:opacity-100 transition-opacity">
                                    ${month.count}
                                </span>
                            </div>
                        </div>
                        <span class="text-xs text-gray-600 font-semibold">${month.count}</span>
                        <span class="text-xs text-gray-500 mt-1">${month.label}</span>
                        <span class="text-xs text-gray-400">${month.year}</span>
                    </div>
                `;
            }).join('');
            
            document.getElementById('monthlyChart').innerHTML = chartHTML;
        }

        function updateDetailedStats(requests) {
            // Top Requesters
            const requesterStats = {};
            requests.forEach(request => {
                if (!requesterStats[request.requesterName]) {
                    requesterStats[request.requesterName] = { count: 0, department: request.department };
                }
                requesterStats[request.requesterName].count++;
            });
            
            const topRequesters = Object.entries(requesterStats)
                .sort(([,a], [,b]) => b.count - a.count)
                .slice(0, 5);
            
            const requestersHTML = topRequesters.map(([name, data], index) => `
                <div class="flex items-center justify-between p-2 rounded-lg hover:bg-gray-50">
                    <div class="flex items-center">
                        <div class="w-6 h-6 bg-blue-500 text-white rounded-full flex items-center justify-center text-xs font-bold mr-2">
                            ${index + 1}
                        </div>
                        <div>
                            <div class="text-sm font-medium text-gray-800">${name}</div>
                            <div class="text-xs text-gray-500">${data.department}</div>
                        </div>
                    </div>
                    <div class="text-sm font-bold text-blue-600">${data.count}</div>
                </div>
            `).join('');
            
            document.getElementById('topRequesters').innerHTML = requestersHTML || 
                '<div class="text-center text-gray-500 py-4">ไม่มีข้อมูล</div>';
            
            // Average Processing Time
            const approvedRequests = requests.filter(r => r.status === 'อนุมัติ' && r.approvedAt);
            let avgDays = 0;
            
            if (approvedRequests.length > 0) {
                const totalDays = approvedRequests.reduce((sum, request) => {
                    const submitted = new Date(request.submittedAt);
                    const approved = new Date(request.approvedAt);
                    const diffTime = Math.abs(approved - submitted);
                    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
                    return sum + diffDays;
                }, 0);
                
                avgDays = Math.round(totalDays / approvedRequests.length * 10) / 10;
            }
            
            document.getElementById('avgProcessingTime').textContent = avgDays > 0 ? avgDays : '-';
            
            // Peak Hours
            const hourStats = {};
            requests.forEach(request => {
                const hour = new Date(request.submittedAt).getHours();
                if (!hourStats[hour]) {
                    hourStats[hour] = 0;
                }
                hourStats[hour]++;
            });
            
            const peakHours = Object.entries(hourStats)
                .sort(([,a], [,b]) => b - a)
                .slice(0, 3);
            
            const peakHoursHTML = peakHours.map(([hour, count], index) => {
                const timeRange = `${String(hour).padStart(2, '0')}:00-${String(parseInt(hour) + 1).padStart(2, '0')}:00`;
                const colors = ['#10B981', '#F59E0B', '#EF4444'];
                
                return `
                    <div class="flex items-center justify-between p-2 rounded-lg hover:bg-gray-50">
                        <div class="flex items-center">
                            <div class="w-6 h-6 text-white rounded-full flex items-center justify-center text-xs font-bold mr-2" 
                                 style="background-color: ${colors[index]}">
                                ${index + 1}
                            </div>
                            <span class="text-sm text-gray-700">${timeRange} น.</span>
                        </div>
                        <span class="text-sm font-bold" style="color: ${colors[index]}">${count}</span>
                    </div>
                `;
            }).join('');
            
            document.getElementById('peakHours').innerHTML = peakHoursHTML || 
                '<div class="text-center text-gray-500 py-4">ไม่มีข้อมูล</div>';
        }

        function refreshReports() {
            // Reload data from localStorage
            currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
            
            // If no requests exist, create sample data
            if (currentRequests.length === 0) {
                createSampleData();
                currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
            }
            
            updateReportsData();
            
            // Show refresh animation
            const refreshBtn = event.target;
            const originalHTML = refreshBtn.innerHTML;
            refreshBtn.innerHTML = '<i class="fas fa-spinner fa-spin mr-2"></i>กำลังรีเฟรช...';
            refreshBtn.disabled = true;
            
            setTimeout(() => {
                refreshBtn.innerHTML = originalHTML;
                refreshBtn.disabled = false;
            }, 1000);
        }

        function exportReport() {
            // Create CSV content
            const headers = ['วันที่ส่งคำขอ', 'ผู้เบิก', 'แผนก', 'รายการ', 'จำนวน', 'หน่วย', 'สถานะ', 'ผู้อนุมัติ'];
            let csvContent = headers.join(',') + '\n';
            
            currentRequests.forEach(request => {
                request.items.forEach(item => {
                    const row = [
                        new Date(request.submittedAt).toLocaleDateString('th-TH'),
                        request.requesterName,
                        request.department,
                        item.item,
                        item.quantity,
                        item.unit,
                        request.status,
                        request.approver || ''
                    ];
                    csvContent += row.map(field => `"${field}"`).join(',') + '\n';
                });
            });
            
            // Create and download file
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            const url = URL.createObjectURL(blob);
            link.setAttribute('href', url);
            link.setAttribute('download', `รายงานการเบิกอุปกรณ์_${new Date().toISOString().split('T')[0]}.csv`);
            link.style.visibility = 'hidden';
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            
            // Show success message
            alert('ส่งออกรายงานเรียบร้อยแล้ว');
        }

        function exportToGoogleSheets() {
            const formData = new FormData(document.getElementById('supplyRequestForm'));
            const sheetUrl = 'https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/edit';
            
            alert('ฟีเจอร์นี้จะเชื่อมต่อกับ Google Sheets API เพื่อส่งข้อมูลโดยอัตโนมัติ\n\nสำหรับการใช้งานจริง กรุณาติดต่อผู้ดูแลระบบเพื่อตั้งค่า Google Sheets Integration');
            
            // In a real implementation, you would:
            // 1. Set up Google Sheets API
            // 2. Create a service account
            // 3. Use the API to append data to the sheet
        }

        function viewRequest(requestId) {
            const request = currentRequests.find(r => r.id === requestId);
            if (request) {
                showRequestDetails(request);
            }
        }

        function showRequestDetails(request) {
            const modal = document.getElementById('requestDetailsModal');
            const content = document.getElementById('requestDetailsContent');
            const actions = document.getElementById('requestActions');
            
            // Populate content
            content.innerHTML = `
                <div class="grid md:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">ผู้เบิก</label>
                        <p class="text-gray-800">${request.requesterName}</p>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">แผนก</label>
                        <p class="text-gray-800">${request.department}</p>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">วันที่ส่งคำขอ</label>
                        <p class="text-gray-800">${new Date(request.submittedAt).toLocaleDateString('th-TH', {
                            year: 'numeric',
                            month: 'long',
                            day: 'numeric',
                            hour: '2-digit',
                            minute: '2-digit'
                        })}</p>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">วันที่ต้องการใช้</label>
                        <p class="text-gray-800">${request.requestDate ? new Date(request.requestDate).toLocaleDateString('th-TH') : 'ไม่ระบุ'}</p>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">ผู้อนุมัติ</label>
                        <p class="text-gray-800">${request.approver || 'ไม่ระบุ'}</p>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">สถานะ</label>
                        <span class="px-3 py-1 text-sm rounded-full ${getStatusColor(request.status)}">
                            ${request.status}
                        </span>
                    </div>
                </div>
                
                <div class="mt-6">
                    <label class="block text-sm font-semibold text-gray-700 mb-2">รายการอุปกรณ์</label>
                    <div class="bg-gray-50 rounded-lg p-4">
                        <div class="space-y-2">
                            ${request.items.map(item => `
                                <div class="flex justify-between items-center py-2 border-b border-gray-200 last:border-b-0">
                                    <span class="text-gray-800">${item.item}</span>
                                    <span class="text-gray-600 font-semibold">${item.quantity} ${item.unit}</span>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                </div>
                
                ${request.remarks ? `
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">หมายเหตุ</label>
                        <p class="text-gray-800 bg-gray-50 p-3 rounded-lg">${request.remarks}</p>
                    </div>
                ` : ''}
            `;
            
            // Populate actions
            if (request.status === 'รอการอนุมัติ') {
                actions.innerHTML = `
                    <button onclick="approveRequest(${request.id})" class="flex-1 bg-green-600 hover:bg-green-700 text-white py-2 px-4 rounded-lg transition-all">
                        <i class="fas fa-check mr-2"></i>อนุมัติ
                    </button>
                    <button onclick="rejectRequest(${request.id})" class="flex-1 bg-red-600 hover:bg-red-700 text-white py-2 px-4 rounded-lg transition-all">
                        <i class="fas fa-times mr-2"></i>ไม่อนุมัติ
                    </button>
                    <button onclick="closeRequestDetails()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-2 px-4 rounded-lg transition-all">
                        ปิด
                    </button>
                `;
            } else {
                actions.innerHTML = `
                    <button onclick="closeRequestDetails()" class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-lg transition-all">
                        ปิด
                    </button>
                `;
            }
            
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

        function closeRequestDetails() {
            document.getElementById('requestDetailsModal').classList.add('hidden');
            document.getElementById('requestDetailsModal').classList.remove('flex');
        }

        function approveRequest(requestId) {
            if (confirm('คุณต้องการอนุมัติคำขอนี้หรือไม่?')) {
                const requestIndex = currentRequests.findIndex(r => r.id === requestId);
                if (requestIndex !== -1) {
                    currentRequests[requestIndex].status = 'อนุมัติ';
                    currentRequests[requestIndex].approvedAt = new Date().toISOString();
                    currentRequests[requestIndex].approvedBy = currentApproverEmail || 'admin';
                    localStorage.setItem('officeSupplyRequests', JSON.stringify(currentRequests));
                    
                    // Send approval email
                    sendApprovalEmail(currentRequests[requestIndex], true);
                    
                    // Update both admin and approver data
                    if (currentApproverEmail) {
                        updateApproverData();
                    } else {
                        updateAdminData();
                    }
                    closeRequestDetails();
                    
                    // Show success message
                    alert('อนุมัติคำขอเรียบร้อยแล้ว');
                }
            }
        }

        function rejectRequest(requestId) {
            const reason = prompt('กรุณาระบุเหตุผลในการไม่อนุมัติ:');
            if (reason !== null && reason.trim() !== '') {
                const requestIndex = currentRequests.findIndex(r => r.id === requestId);
                if (requestIndex !== -1) {
                    currentRequests[requestIndex].status = 'ไม่อนุมัติ';
                    currentRequests[requestIndex].rejectedAt = new Date().toISOString();
                    currentRequests[requestIndex].rejectionReason = reason;
                    currentRequests[requestIndex].rejectedBy = currentApproverEmail || 'admin';
                    localStorage.setItem('officeSupplyRequests', JSON.stringify(currentRequests));
                    
                    // Send rejection email
                    sendApprovalEmail(currentRequests[requestIndex], false);
                    
                    // Update both admin and approver data
                    if (currentApproverEmail) {
                        updateApproverData();
                    } else {
                        updateAdminData();
                    }
                    closeRequestDetails();
                    
                    // Show success message
                    alert('ไม่อนุมัติคำขอเรียบร้อยแล้ว');
                }
            }
        }

        function sendApprovalEmail(requestData, isApproved) {
            const subject = `${isApproved ? 'อนุมัติ' : 'ไม่อนุมัติ'}คำขอเบิกอุปกรณ์สำนักงาน - ${requestData.requesterName}`;
            const body = `
เรียน ${requestData.requesterName}

${isApproved ? 'คำขอเบิกอุปกรณ์สำนักงานของท่านได้รับการอนุมัติแล้ว' : 'คำขอเบิกอุปกรณ์สำนักงานของท่านไม่ได้รับการอนุมัติ'}

รายละเอียดคำขอ:
แผนก: ${requestData.department}
วันที่ส่งคำขอ: ${new Date(requestData.submittedAt).toLocaleDateString('th-TH')}

รายการอุปกรณ์:
${requestData.items.map(item => `- ${item.item} จำนวน ${item.quantity} ${item.unit}`).join('\n')}

${!isApproved && requestData.rejectionReason ? `เหตุผลที่ไม่อนุมัติ: ${requestData.rejectionReason}` : ''}

${isApproved ? 'กรุณาติดต่อเจ้าหน้าที่เพื่อรับอุปกรณ์' : 'หากมีข้อสงสัย กรุณาติดต่อผู้อนุมัติ'}

ขอบคุณครับ/ค่ะ
            `;

            // In a real system, you would send this email automatically
            // For demo purposes, we'll open the email client
            const mailtoLink = `mailto:${requestData.requesterName}@taisin.co.th?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
            window.open(mailtoLink);
        }

        // Approver management functions
        function updateApproversList() {
            const approversList = document.getElementById('approversList');
            approversList.innerHTML = '';
            
            approvers.forEach(approver => {
                const approverCard = document.createElement('div');
                approverCard.className = 'bg-white p-4 rounded-lg border flex items-center justify-between';
                approverCard.innerHTML = `
                    <div>
                        <p class="font-semibold text-gray-800">${approver.email}</p>
                        <p class="text-sm text-gray-600">${approver.position}</p>
                    </div>
                    <div class="flex space-x-2">
                        <button onclick="editApprover('${approver.email}')" class="text-blue-600 hover:text-blue-800">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button onclick="deleteApprover('${approver.email}')" class="text-red-600 hover:text-red-800">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                `;
                approversList.appendChild(approverCard);
            });
        }

        function showAddApprover() {
            editingApprover = null;
            document.getElementById('approverModalTitle').textContent = 'เพิ่มผู้อนุมัติ';
            document.getElementById('approverEmail').value = '';
            document.getElementById('approverPosition').value = '';
            document.getElementById('approverModal').classList.remove('hidden');
            document.getElementById('approverModal').classList.add('flex');
        }

        function editApprover(email) {
            const approver = approvers.find(a => a.email === email);
            if (approver) {
                editingApprover = email;
                document.getElementById('approverModalTitle').textContent = 'แก้ไขผู้อนุมัติ';
                document.getElementById('approverEmail').value = approver.email;
                document.getElementById('approverPosition').value = approver.position;
                document.getElementById('approverModal').classList.remove('hidden');
                document.getElementById('approverModal').classList.add('flex');
            }
        }

        function deleteApprover(email) {
            if (confirm('คุณต้องการลบผู้อนุมัติคนนี้หรือไม่?')) {
                approvers = approvers.filter(a => a.email !== email);
                localStorage.setItem('approvers', JSON.stringify(approvers));
                updateApproversList();
                updateApproverDropdown();
            }
        }

        function closeApproverModal() {
            document.getElementById('approverModal').classList.add('hidden');
            document.getElementById('approverModal').classList.remove('flex');
        }

        // Approver form submission
        document.getElementById('approverForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const email = document.getElementById('approverEmail').value;
            const position = document.getElementById('approverPosition').value;
            
            if (editingApprover) {
                // Edit existing approver
                const index = approvers.findIndex(a => a.email === editingApprover);
                if (index !== -1) {
                    approvers[index] = { email, position };
                }
            } else {
                // Add new approver
                if (approvers.find(a => a.email === email)) {
                    alert('อีเมลนี้มีอยู่แล้ว');
                    return;
                }
                approvers.push({ email, position });
            }
            
            localStorage.setItem('approvers', JSON.stringify(approvers));
            updateApproversList();
            updateApproverDropdown();
            closeApproverModal();
        });

        function updateApproverData() {
            console.log('Updating approver data...');
            
            // Reload data from localStorage to ensure we have latest data
            currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
            console.log('Total requests loaded:', currentRequests.length);
            
            // If no requests exist, create sample data
            if (currentRequests.length === 0) {
                console.log('No requests found, creating sample data...');
                createSampleData();
                currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
            }
            
            // Show ALL requests for approver (not filtering by approver email)
            const approverRequests = currentRequests;
            
            const pendingRequests = approverRequests.filter(r => r.status === 'รอการอนุมัติ').length;
            const approvedRequests = approverRequests.filter(r => r.status === 'อนุมัติ').length;
            const rejectedRequests = approverRequests.filter(r => r.status === 'ไม่อนุมัติ').length;

            console.log('Stats - Pending:', pendingRequests, 'Approved:', approvedRequests, 'Rejected:', rejectedRequests);

            // Update summary cards
            const pendingElement = document.getElementById('approverPendingRequests');
            const approvedElement = document.getElementById('approverApprovedRequests');
            const rejectedElement = document.getElementById('approverRejectedRequests');
            
            if (pendingElement) pendingElement.textContent = pendingRequests;
            if (approvedElement) approvedElement.textContent = approvedRequests;
            if (rejectedElement) rejectedElement.textContent = rejectedRequests;

            // Update requests table
            updateApproverRequestsTable();
        }

        function updateApproverRequestsTable() {
            console.log('Updating approver requests table...');
            
            // Ensure we have current data
            if (currentRequests.length === 0) {
                console.log('No requests found, creating sample data...');
                createSampleData();
                currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
            }
            
            // Show ALL requests in the system for approver view
            let filteredRequests = [...currentRequests];
            console.log('Total requests before filtering:', filteredRequests.length);
            
            // Apply filters
            const statusFilter = document.getElementById('statusFilter')?.value || '';
            const departmentFilter = document.getElementById('departmentFilter')?.value || '';
            
            if (statusFilter) {
                filteredRequests = filteredRequests.filter(r => r.status === statusFilter);
                console.log('After status filter:', filteredRequests.length);
            }
            
            if (departmentFilter) {
                filteredRequests = filteredRequests.filter(r => r.department === departmentFilter);
                console.log('After department filter:', filteredRequests.length);
            }
            
            const tableBody = document.getElementById('approverRequestsTable');
            
            if (!tableBody) {
                console.error('Table body element not found!');
                return;
            }
            
            if (filteredRequests.length === 0) {
                tableBody.innerHTML = '<tr><td colspan="7" class="px-6 py-8 text-center text-gray-500">ไม่มีข้อมูลคำขอที่ตรงกับเงื่อนไข</td></tr>';
            } else {
                console.log('Rendering', filteredRequests.length, 'requests');
                tableBody.innerHTML = filteredRequests.sort((a, b) => new Date(b.submittedAt) - new Date(a.submittedAt)).map(request => `
                    <tr class="border-t hover:bg-gray-50">
                        <td class="px-6 py-4 text-sm text-gray-700">${new Date(request.submittedAt).toLocaleDateString('th-TH', {
                            year: 'numeric',
                            month: 'short',
                            day: 'numeric'
                        })}</td>
                        <td class="px-6 py-4 text-sm text-gray-700 font-medium">${request.requesterName}</td>
                        <td class="px-6 py-4 text-sm text-gray-700">${request.department}</td>
                        <td class="px-6 py-4 text-sm text-gray-700">${request.requestDate ? new Date(request.requestDate).toLocaleDateString('th-TH', {
                            month: 'short',
                            day: 'numeric'
                        }) : 'ไม่ระบุ'}</td>
                        <td class="px-6 py-4 text-sm text-gray-700 text-center">
                            <span class="bg-blue-100 text-blue-800 px-2 py-1 rounded-full text-xs font-semibold">
                                ${request.items.length} รายการ
                            </span>
                        </td>
                        <td class="px-6 py-4">
                            <span class="px-3 py-1 text-xs rounded-full font-semibold ${getStatusColor(request.status)}">
                                ${request.status}
                            </span>
                        </td>
                        <td class="px-6 py-4">
                            <div class="flex space-x-2">
                                <button onclick="viewRequest(${request.id})" class="text-blue-600 hover:text-blue-800 text-sm font-medium">
                                    <i class="fas fa-eye mr-1"></i>ดูรายละเอียด
                                </button>
                                ${request.status === 'รอการอนุมัติ' ? `
                                    <button onclick="quickApprove(${request.id})" class="text-green-600 hover:text-green-800 text-sm font-medium">
                                        <i class="fas fa-check mr-1"></i>อนุมัติ
                                    </button>
                                    <button onclick="quickReject(${request.id})" class="text-red-600 hover:text-red-800 text-sm font-medium">
                                        <i class="fas fa-times mr-1"></i>ไม่อนุมัติ
                                    </button>
                                ` : ''}
                            </div>
                        </td>
                    </tr>
                `).join('');
            }
        }

        function filterApproverRequests() {
            updateApproverRequestsTable();
        }

        function refreshApproverData() {
            // Reload data from localStorage
            currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
            updateApproverData();
            
            // Show refresh animation
            const refreshBtn = event.target;
            const originalHTML = refreshBtn.innerHTML;
            refreshBtn.innerHTML = '<i class="fas fa-spinner fa-spin mr-2"></i>กำลังรีเฟรช...';
            refreshBtn.disabled = true;
            
            setTimeout(() => {
                refreshBtn.innerHTML = originalHTML;
                refreshBtn.disabled = false;
            }, 1000);
        }

        function quickApprove(requestId) {
            if (confirm('คุณต้องการอนุมัติคำขอนี้หรือไม่?')) {
                const requestIndex = currentRequests.findIndex(r => r.id === requestId);
                if (requestIndex !== -1) {
                    currentRequests[requestIndex].status = 'อนุมัติ';
                    currentRequests[requestIndex].approvedAt = new Date().toISOString();
                    currentRequests[requestIndex].approvedBy = currentApproverEmail;
                    localStorage.setItem('officeSupplyRequests', JSON.stringify(currentRequests));
                    
                    // Send approval email
                    sendApprovalEmail(currentRequests[requestIndex], true);
                    
                    updateApproverData();
                    
                    // Show success message
                    alert('อนุมัติคำขอเรียบร้อยแล้ว');
                }
            }
        }

        function quickReject(requestId) {
            const reason = prompt('กรุณาระบุเหตุผลในการไม่อนุมัติ:');
            if (reason !== null && reason.trim() !== '') {
                const requestIndex = currentRequests.findIndex(r => r.id === requestId);
                if (requestIndex !== -1) {
                    currentRequests[requestIndex].status = 'ไม่อนุมัติ';
                    currentRequests[requestIndex].rejectedAt = new Date().toISOString();
                    currentRequests[requestIndex].rejectionReason = reason;
                    currentRequests[requestIndex].rejectedBy = currentApproverEmail;
                    localStorage.setItem('officeSupplyRequests', JSON.stringify(currentRequests));
                    
                    // Send rejection email
                    sendApprovalEmail(currentRequests[requestIndex], false);
                    
                    updateApproverData();
                    
                    // Show success message
                    alert('ไม่อนุมัติคำขอเรียบร้อยแล้ว');
                }
            }
        }

        // Admin approval functions
        function adminApproveRequest(requestId) {
            console.log('Admin approving request:', requestId);
            if (confirm('คุณต้องการอนุมัติคำขอนี้หรือไม่?')) {
                // Reload current requests to ensure we have latest data
                currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
                
                const requestIndex = currentRequests.findIndex(r => r.id == requestId);
                console.log('Found request at index:', requestIndex);
                
                if (requestIndex !== -1) {
                    currentRequests[requestIndex].status = 'อนุมัติ';
                    currentRequests[requestIndex].approvedAt = new Date().toISOString();
                    currentRequests[requestIndex].approvedBy = 'admin';
                    
                    // Save to localStorage
                    localStorage.setItem('officeSupplyRequests', JSON.stringify(currentRequests));
                    console.log('Request approved and saved');
                    
                    // Send approval email
                    sendApprovalEmail(currentRequests[requestIndex], true);
                    
                    // Update admin data display
                    updateAdminData();
                    
                    // Show success message
                    alert('อนุมัติคำขอเรียบร้อยแล้ว');
                } else {
                    console.error('Request not found with ID:', requestId);
                    alert('ไม่พบคำขอที่ต้องการอนุมัติ');
                }
            }
        }

        function adminRejectRequest(requestId) {
            console.log('Admin rejecting request:', requestId);
            const reason = prompt('กรุณาระบุเหตุผลในการไม่อนุมัติ:');
            if (reason !== null && reason.trim() !== '') {
                // Reload current requests to ensure we have latest data
                currentRequests = JSON.parse(localStorage.getItem('officeSupplyRequests') || '[]');
                
                const requestIndex = currentRequests.findIndex(r => r.id == requestId);
                console.log('Found request at index:', requestIndex);
                
                if (requestIndex !== -1) {
                    currentRequests[requestIndex].status = 'ไม่อนุมัติ';
                    currentRequests[requestIndex].rejectedAt = new Date().toISOString();
                    currentRequests[requestIndex].rejectionReason = reason;
                    currentRequests[requestIndex].rejectedBy = 'admin';
                    
                    // Save to localStorage
                    localStorage.setItem('officeSupplyRequests', JSON.stringify(currentRequests));
                    console.log('Request rejected and saved');
                    
                    // Send rejection email
                    sendApprovalEmail(currentRequests[requestIndex], false);
                    
                    // Update admin data display
                    updateAdminData();
                    
                    // Show success message
                    alert('ไม่อนุมัติคำขอเรียบร้อยแล้ว');
                } else {
                    console.error('Request not found with ID:', requestId);
                    alert('ไม่พบคำขอที่ต้องการไม่อนุมัติ');
                }
            }
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            showWelcome();
            updateApproverDropdown();
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'96f5b734d1027b40',t:'MTc1NTIyOTY5OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

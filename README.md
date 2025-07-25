<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>有代價地就罪行不予檢控計算器</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Microsoft JhengHei", "微軟正黑體", sans-serif;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            color: #343a40;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        /* 页头样式 - Logo和标题 */
        .header {
            display: flex;
            align-items: center;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            padding: 15px 25px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }
        
        .logo-container {
            display: flex;
            align-items: center;
            margin-right: 25px;
        }
        
        .customs-logo {
            height: 70px;
            width: auto;
            margin-right: 20px;
        }
        
        .title-container {
            flex: 1;
            min-width: 300px;
        }
        
        .page-title {
            font-size: 1.8rem;
            font-weight: 700;
            color: #1a237e;
            margin-bottom: 5px;
        }
        
        .page-subtitle {
            font-size: 1rem;
            color: #5c6bc0;
            font-weight: 500;
        }
        
        /* 计算器样式 */
        .calculator {
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
            margin-bottom: 30px;
        }
        
        .calculator-header {
            text-align: center;
            margin-bottom: 25px;
        }
        
        .calculator-title {
            font-size: 1.5rem;
            color: #1a237e;
            margin-bottom: 10px;
        }
        
        .calculator-description {
            color: #5c6bc0;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .calc-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 16px 0;
            border-bottom: 1px solid #edf2f7;
            transition: background-color 0.2s;
        }
        
        .calc-item:hover {
            background-color: #f8f9ff;
        }
        
        .item-label {
            color: #2c3e50;
            font-size: 16px;
            width: 65%;
            line-height: 1.5;
        }
        
        .item-value {
            font-weight: 600;
            text-align: right;
            width: 35%;
            color: #1a73e8;
            font-size: 16px;
        }
        
        .input-container {
            position: relative;
        }
        
        input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #c5cae9;
            border-radius: 8px;
            font-size: 16px;
            text-align: right;
            color: #2c3e50;
            background: #f8f9ff;
            transition: all 0.3s;
        }
        
        input:focus {
            border-color: #5c6bc0;
            background: white;
            outline: none;
            box-shadow: 0 0 0 3px rgba(92, 107, 192, 0.2);
        }
        
        .unit {
            color: #64748b;
            font-size: 0.9em;
            margin-left: 4px;
        }
        
        .calc-total {
            background: #e8eaf6;
            border-radius: 8px;
            margin-top: 10px;
        }
        
        .highlight {
            color: #d32f2f;
            font-weight: 700;
        }
        
        .info-note {
            font-size: 14px;
            color: #666;
            margin-top: 5px;
            font-style: italic;
        }
        
        /* 免責聲明樣式 */
        .disclaimer {
            background: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            border-top: 3px solid #5c6bc0;
        }
        
        .disclaimer-title {
            text-align: center;
            font-size: 1.2rem;
            color: #d32f2f;
            margin-bottom: 15px;
            font-weight: 600;
        }
        
        .disclaimer-content {
            font-size: 14px;
            color: #555;
            line-height: 1.7;
        }
        
        .disclaimer-content a {
            color: #1a73e8;
            text-decoration: none;
            font-weight: 500;
        }
        
        .disclaimer-content a:hover {
            text-decoration: underline;
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                text-align: center;
                padding: 20px;
            }
            
            .logo-container {
                margin-right: 0;
                margin-bottom: 15px;
                justify-content: center;
            }
            
            .title-container {
                min-width: auto;
            }
            
            .page-title {
                font-size: 1.5rem;
            }
            
            .calculator {
                padding: 20px;
            }
            
            .calc-item {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .item-label, .item-value {
                width: 100%;
                text-align: left;
            }
            
            .item-value {
                margin-top: 8px;
            }
            
            input {
                text-align: left;
            }
        }
        
        @media (max-width: 480px) {
            .page-title {
                font-size: 1.3rem;
            }
            
            .calculator-title {
                font-size: 1.3rem;
            }
        }
        
        /* 动画效果 */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .calculator, .disclaimer {
            animation: fadeIn 0.6s ease-out forwards;
        }
        
        .disclaimer {
            animation-delay: 0.2s;
        }
        
        /* 打印样式 */
        @media print {
            body {
                background: white;
                padding: 10px;
            }
            
            .header, .calculator, .disclaimer {
                box-shadow: none;
                border: 1px solid #ddd;
            }
            
            .disclaimer {
                page-break-before: avoid;
                page-break-inside: avoid;
            }
            
            button {
                display: none;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 页头部分 - Logo和标题 -->
        <header class="header">
            <div class="logo-container">
                <img src="https://upload.wikimedia.org/wikipedia/zh/thumb/8/82/Customs_and_Excise_Department_%28Hong_Kong%29.svg/1200px-Customs_and_Excise_Department_%28Hong_Kong%29.svg.png" 
                     alt="香港海關 Hong Kong Customs" 
                     class="customs-logo">
            </div>
            <div class="title-container">
                <h1 class="page-title">有代價地就罪行不予檢控計算器</h1>
                <p class="page-subtitle">香港海關專用工具 - 罰款金額計算</p>
            </div>
        </header>
        
        <!-- 计算器主体 -->
        <main class="calculator">
            <div class="calculator-header">
                <h2 class="calculator-title">香煙罰款計算器</h2>
                <p class="calculator-description">輸入檢取香煙總數，系統將自動計算各項罰款金額</p>
            </div>
            
            <!-- 輸入項 -->
            <div class="calc-item">
                <div class="item-label">a. 檢取香煙總數</div>
                <div class="item-value">
                    <div class="input-container">
                        <input type="number" id="totalCigarettes" placeholder="輸入數量" min="0">
                    </div>
                    <div class="info-note">免稅額：19枝</div>
                </div>
            </div>
            
            <!-- 計算結果 -->
            <div class="calc-item">
                <div class="item-label">b. 除19枝免稅額以外的香煙數量</div>
                <div class="item-value"><span id="b">-</span></div>
            </div>
            
            <div class="calc-item">
                <div class="item-label">c. 香煙金額</div>
                <div class="item-value">$<span id="c">-</span> <span class="unit">(每根$4.1)</span></div>
            </div>
            
            <div class="calc-item">
                <div class="item-label">d. 香煙應課稅額</div>
                <div class="item-value">$<span id="d">-</span> <span class="unit">(每根$3.306)</span></div>
            </div>
            
            <div class="calc-item">
                <div class="item-label">e. 應課稅額5倍罰款</div>
                <div class="item-value">$<span id="e">-</span> <span class="unit">(5倍計算)</span></div>
            </div>
            
            <div class="calc-item">
                <div class="item-label">f. 未申報定額罰款</div>
                <div class="item-value">$2,000</div>
            </div>
            
            <div class="calc-item calc-total">
                <div class="item-label" style="font-weight:600;">g. 罰款總額</div>
                <div class="item-value" style="color:#d32f2f;font-weight:700;">$<span id="g">-</span></div>
            </div>
        </main>
        
        <!-- 免責聲明 -->
        <div class="disclaimer">
            <h3 class="disclaimer-title">免責聲明</h3>
            <div class="disclaimer-content">
                <p>本計算器提供之結果僅供參考之用，香港海關不對其準確性或完整性承擔任何責任。任何人士因依賴本內容而引致的損失，香港海關概不負責。本計算結果不構成任何法律建議或正式罰款通知。</p>
                <p>實際罰款金額可能因個案情況、法例更新及其他相關因素而有所調整。使用者應以香港海關正式通知為準，並在需要時尋求專業法律意見。</p>
                <p>查閱最新官方資訊及相關法例，請瀏覽<a href="https://www.customs.gov.hk" target="_blank">香港海關官方網站</a>。</p>
            </div>
        </div>
    </div>

    <script>
        function formatNumber(num) {
            // 处理负数情况
            const absNum = Math.abs(num);
            const formatted = absNum.toLocaleString('en-US', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            });
            
            return num < 0 ? `-${formatted}` : formatted;
        }

        function calculate() {
            // 獲取輸入值
            const a = parseInt(document.getElementById('totalCigarettes').value) || 0;
            
            // 分步計算
            const b = Math.max(a - 19, 0);  // 確保不低於0
            const c = b * 4.1;
            const d = b * 3.306;
            const e = d * 5;
            const f = 2000;
            const g = e + f;
            
            // 更新顯示
            document.getElementById('b').textContent = b;
            document.getElementById('c').textContent = formatNumber(c);
            document.getElementById('d').textContent = formatNumber(d);
            document.getElementById('e').textContent = formatNumber(e);
            document.getElementById('g').textContent = formatNumber(g);
            
            // 更新总额高亮
            const totalElement = document.getElementById('g');
            if (g > 10000) {
                totalElement.parentElement.style.color = '#b71c1c';
            } else {
                totalElement.parentElement.style.color = '#d32f2f';
            }
        }
        
        // 初始计算
        calculate();
        
        // 即時計算
        document.getElementById('totalCigarettes').addEventListener('input', calculate);
        
        // 添加键盘快捷键
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                document.getElementById('totalCigarettes').value = '';
                calculate();
            }
        });
    </script>
</body>
</html>

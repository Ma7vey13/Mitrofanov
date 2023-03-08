</head>

<body class="fullcontent">

<div id="quarto-content" class="page-columns page-rows-contents page-layout-article">

<main class="content" id="quarto-document-content">



<section id="системы-аутентификациии-и-защиты-от-несанкционированного-доступа" class="level1">
<h1>Системы аутентификациии и защиты от несанкционированного доступа</h1>
<p>Практическая работа №1</p>
<section id="цель" class="level2">
<h2 class="anchored" data-anchor-id="цель">Цель</h2>
<p>Вывести информацию о системе</p>
</section>
<section id="исходные-данные" class="level2">
<h2 class="anchored" data-anchor-id="исходные-данные">Исходные данные</h2>
<ol type="1">
<li>ОС Windows 11</li>
<li>RStudio Desktop</li>
<li>Интерпретатор языка R 4.2.2</li>
</ol>
</section>
<section id="план" class="level2">
<h2 class="anchored" data-anchor-id="план">План</h2>
<ol type="1">
<li>Выполнить команду system2(“systeminfo”, stdout = TRUE)</li>
<li>Выполнить команду system(“wmic cpu get name”)</li>
<li>Выполнить команду system(“powershell.exe”, args = c(“Get-EventLog”, “-LogName”, “System”, “-Newest”, “30”), stdout = TRUE)</li>
</ol>
</section>
<section id="шаги" class="level2">
<h2 class="anchored" data-anchor-id="шаги">Шаги</h2>
<ol type="1">
<li>Выполнение команды system2(“systeminfo”, stdout = TRUE) для вывод информации о системе windows</li>
</ol>
<div class="cell">
<div class="sourceCode cell-code" id="cb1"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="fu">system2</span>(<span class="st">"systeminfo"</span>, <span class="at">stdout =</span> <span class="cn">TRUE</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code> [1] ""                                                                                           
 [2] "Host Name:                 LAPTOP-NOIR"                                                     
 [3] "OS Name:                   Microsoft Windows 11 Home Single Language"                       
 [4] "OS Version:                10.0.22621 N/A Build 22621"                                      
 [5] "OS Manufacturer:           Microsoft Corporation"                                           
 [6] "OS Configuration:          Standalone Workstation"                                          
 [7] "OS Build Type:             Multiprocessor Free"                                             
 [8] "Registered Owner:          Matvey"                                                          
 [9] "Registered Organization:   N/A"                                                             
[10] "Product ID:                00342-43230-52351-AAOEM"                                         
[11] "Original Install Date:     11.02.2023, 1:59:18"                                             
[12] "System Boot Time:          08.03.2023, 16:38:49"                                            
[13] "System Manufacturer:       HUAWEI"                                                          
[14] "System Model:              CREM-WXX9"                                                       
[15] "System Type:               x64-based PC"                                                    
[16] "Processor(s):              1 Processor(s) Installed."                                       
[17] "                           [01]: AMD64 Family 25 Model 80 Stepping 0 AuthenticAMD ~3201 Mhz"
[18] "BIOS Version:              HUAWEI 2.26, 13.05.2022"                                         
[19] "Windows Directory:         C:\\WINDOWS"                                                     
[20] "System Directory:          C:\\WINDOWS\\system32"                                           
[21] "Boot Device:               \\Device\\HarddiskVolume1"                                       
[22] "System Locale:             ru;Russian"                                                      
[23] "Input Locale:              ru;Russian"                                                      
[24] "Time Zone:                 (UTC+03:00) Moscow, St. Petersburg"                              
[25] "Total Physical Memory:     15&nbsp;724 MB"                                                       
[26] "Available Physical Memory: 8&nbsp;523 MB"                                                        
[27] "Virtual Memory: Max Size:  24&nbsp;428 MB"                                                       
[28] "Virtual Memory: Available: 16&nbsp;559 MB"                                                       
[29] "Virtual Memory: In Use:    7&nbsp;869 MB"                                                        
[30] "Page File Location(s):     C:\\pagefile.sys"                                                
[31] "Domain:                    WORKGROUP"                                                       
[32] "Logon Server:              \\\\LAPTOP-NOIR"                                                 
[33] "Hotfix(s):                 4 Hotfix(s) Installed."                                          
[34] "                           [01]: KB5022497"                                                 
[35] "                           [02]: KB5012170"                                                 
[36] "                           [03]: KB5022845"                                                 
[37] "                           [04]: KB5022610"                                                 
[38] "Network Card(s):           1 NIC(s) Installed."                                             
[39] "                           [01]: Realtek 8822CE Wireless LAN 802.11ac PCI-E NIC"            
[40] "                                 Connection Name: Беспроводная сеть"                        
[41] "                                 DHCP Enabled:    Yes"                                      
[42] "                                 DHCP Server:     192.168.1.1"                              
[43] "                                 IP address(es)"                                            
[44] "                                 [01]: 192.168.1.3"                                         
[45] "                                 [02]: fe80::30b7:b072:210c:1e55"                           
[46] "Hyper-V Requirements:      VM Monitor Mode Extensions: Yes"                                 
[47] "                           Virtualization Enabled In Firmware: Yes"                         
[48] "                           Second Level Address Translation: Yes"                           
[49] "                           Data Execution Prevention Available: Yes"                        </code></pre>
</div>
</div>
<ol start="2" type="1">
<li>Выполнение команды system(“wmic cpu get name”) для информации о процессоре</li>
</ol>
<div class="cell">
<div class="sourceCode cell-code" id="cb3"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="fu">system2</span>(<span class="st">"cmd"</span>, <span class="at">args =</span> <span class="fu">c</span>(<span class="st">"/c"</span>, <span class="st">"wmic cpu get name"</span>), <span class="at">stdout =</span> <span class="cn">TRUE</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] "Name                                    \r"
[2] "AMD Ryzen 7 5800H with Radeon Graphics  \r"
[3] "\r"                                        </code></pre>
</div>
</div>
<ol start="3" type="1">
<li>Выполнение команды system(“powershell.exe”, args = c(“Get-EventLog”, “-LogName”, “System”, “-Newest”, “30”), stdout = TRUE) для получение информации о логах</li>
</ol>
<div class="cell">
<div class="sourceCode cell-code" id="cb5"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb5-1"><a href="#cb5-1" aria-hidden="true" tabindex="-1"></a><span class="fu">system2</span>(<span class="st">"powershell.exe"</span>, <span class="at">args =</span> <span class="fu">c</span>(<span class="st">"Get-EventLog"</span>, <span class="st">"-LogName"</span>, <span class="st">"System"</span>, <span class="st">"-Newest"</span>, <span class="st">"30"</span>), <span class="at">stdout =</span> <span class="cn">TRUE</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code> [1] ""                                                                                                                       
 [2] "   Index Time          EntryType   Source                 InstanceID Message                                           "
 [3] "   ----- ----          ---------   ------                 ---------- -------                                           "
 [4] "    6254 мар 08 16:51  Information Service Control M...   1073748864 The start type of the Фоновая интеллектуальная ..."
 [5] "    6253 мар 08 16:49  Information Service Control M...   1073748864 The start type of the Фоновая интеллектуальная ..."
 [6] "    6252 мар 08 16:41  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
 [7] "    6251 мар 08 16:41  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
 [8] "    6250 мар 08 16:41  Information Service Control M...   1073748864 The start type of the Фоновая интеллектуальная ..."
 [9] "    6249 мар 08 16:40  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[10] "    6248 мар 08 16:40  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[11] "    6247 мар 08 16:40  Information Microsoft-Windows...          158 The time provider 'VMICTimeProvider' has indica..."
[12] "    6246 мар 08 16:40  Error       DCOM                        10010 The description for Event ID '10010' in Source ..."
[13] "    6245 мар 08 16:39  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[14] "    6244 мар 08 16:39  Information Microsoft-Windows...          113 Attempted to add URL (http://localhost:5426/) t..."
[15] "    6243 мар 08 16:39  Information Microsoft-Windows...          111 Create URL group 18302628907645403137. Status 0..."
[16] "    6242 мар 08 16:39  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[17] "    6241 мар 08 16:39  Information Microsoft-Windows...         1025 The TPM was successfully provisioned and is now..."
[18] "    6240 мар 08 16:39  Information Microsoft-Windows...         1282 The TBS device identifier has been generated.     "
[19] "    6239 мар 08 16:39  Information Service Control M...   1073748864 The start type of the Фоновая интеллектуальная ..."
[20] "    6238 мар 08 16:38  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[21] "    6237 мар 08 16:38  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[22] "    6236 мар 08 16:38  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[23] "    6235 мар 08 16:38  Warning     DCOM                        10016 The description for Event ID '10016' in Source ..."
[24] "    6234 мар 08 16:38  Information TPM                            18 This event triggers the Trusted Platform Module..."
[25] "    6233 мар 08 16:38  Information Service Control M...   3221232498 The following boot-start or system-start driver..."
[26] "    6232 мар 08 16:38  Information Microsoft-Windows...         7001 User Logon Notification for Customer Experience..."
[27] "    6231 мар 08 16:38  Error       Service Control M...   3221232472 The Focusrite Control Server service failed to ..."
[28] "    6230 мар 08 16:38  Information Microsoft-Windows...         4000 WLAN AutoConfig service has successfully starte..."
[29] "    6229 мар 08 16:38  Information Microsoft-Windows...          112 Attempted to reserve URL http://+:10243/WMPNSSv..."
[30] "    6228 мар 08 16:38  Information Microsoft-Windows...          112 Attempted to reserve URL https://+:10245/WMPNSS..."
[31] "    6227 мар 08 16:38  Information Microsoft-Windows...          112 Attempted to reserve URL http://+:3387/rdp/. St..."
[32] "    6226 мар 08 16:38  Information Microsoft-Windows...          112 Attempted to reserve URL https://+:3392/rdp/. S..."
[33] "    6225 мар 08 16:38  Information Microsoft-Windows...          112 Attempted to reserve URL http://+:10246/MDEServ..."
[34] ""                                                                                                                       
[35] ""                                                                                                                       </code></pre>
</div>
</div>
</section>
<section id="оценка-результата" class="level2">
<h2 class="anchored" data-anchor-id="оценка-результата">Оценка результата</h2>
<p>В результате лабораторной работы мы получили основную информацию об ОС, процессоре и логи системы.</p>
</section>
<section id="вывод" class="level2">
<h2 class="anchored" data-anchor-id="вывод">Вывод</h2>
<p>Таким образом были получены навыки работы с командыми windows с помощью языка R</p>
</section>
</section>

</div> <!-- /content -->



</body></html>
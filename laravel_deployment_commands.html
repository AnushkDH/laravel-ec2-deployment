<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Laravel EC2 Deployment Guide</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Segoe UI', system-ui, sans-serif;
    background: #f0f2f5;
    color: #1a1a2e;
    line-height: 1.6;
  }

  header {
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 60%, #0f3460 100%);
    color: white;
    padding: 40px 48px 32px;
    border-bottom: 4px solid #e94560;
  }

  header h1 {
    font-size: 28px;
    font-weight: 700;
    letter-spacing: -0.5px;
  }

  header p {
    margin-top: 8px;
    color: #a0aec0;
    font-size: 14px;
  }

  .badge {
    display: inline-block;
    padding: 3px 10px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 600;
    margin-right: 6px;
    margin-top: 10px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .badge-nginx  { background: #27ae60; color: white; }
  .badge-php    { background: #8892be; color: white; }
  .badge-mysql  { background: #e67e22; color: white; }
  .badge-ubuntu { background: #e94560; color: white; }

  .container { max-width: 900px; margin: 0 auto; padding: 40px 24px; }

  /* Part headers */
  .part-header {
    display: flex;
    align-items: center;
    gap: 14px;
    margin: 40px 0 20px;
  }

  .part-label {
    background: #e94560;
    color: white;
    font-size: 11px;
    font-weight: 700;
    padding: 4px 12px;
    border-radius: 4px;
    text-transform: uppercase;
    letter-spacing: 1px;
    white-space: nowrap;
  }

  .part-label.part2 { background: #0f3460; }

  .part-title {
    font-size: 18px;
    font-weight: 700;
    color: #1a1a2e;
  }

  .part-desc {
    font-size: 13px;
    color: #718096;
    margin-bottom: 24px;
    padding-left: 4px;
  }

  /* Step cards */
  .step {
    background: white;
    border-radius: 10px;
    margin-bottom: 16px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.07);
    overflow: hidden;
    border-left: 4px solid #e94560;
  }

  .step.project { border-left-color: #0f3460; }

  .step-header {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 14px 20px;
    cursor: pointer;
    user-select: none;
  }

  .step-num {
    background: #e94560;
    color: white;
    font-size: 12px;
    font-weight: 700;
    width: 28px;
    height: 28px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  .step.project .step-num { background: #0f3460; }

  .step-title {
    font-size: 15px;
    font-weight: 600;
    color: #1a1a2e;
    flex: 1;
  }

  .step-body { padding: 0 20px 16px; }

  /* Code blocks */
  .code-label {
    font-size: 10px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #a0aec0;
    margin-bottom: 4px;
    margin-top: 12px;
  }

  pre {
    background: #1a1a2e;
    border-radius: 8px;
    padding: 16px 18px;
    overflow-x: auto;
    font-size: 13px;
    line-height: 1.7;
  }

  /* Command types - color coding */
  .cmd-sudo   { color: #e94560; font-weight: 600; }   /* sudo = red */
  .cmd-php    { color: #8892be; font-weight: 600; }   /* php = purple */
  .cmd-composer { color: #f6c90e; font-weight: 600; } /* composer = yellow */
  .cmd-npm    { color: #68d391; font-weight: 600; }   /* npm = green */
  .cmd-git    { color: #63b3ed; font-weight: 600; }   /* git = blue */
  .cmd-mysql  { color: #e67e22; font-weight: 600; }   /* mysql keywords = orange */
  .cmd-default { color: #e2e8f0; }                    /* default = light grey */
  .cmd-comment { color: #4a5568; font-style: italic; } /* comments = dark grey */
  .cmd-key    { color: #81e6d9; }                     /* env keys = teal */
  .cmd-val    { color: #fbd38d; }                     /* env values = peach */
  .cmd-flag   { color: #a0aec0; }                     /* flags like -y -R = grey */

  .note {
    background: #fffbeb;
    border: 1px solid #fcd34d;
    border-radius: 6px;
    padding: 10px 14px;
    font-size: 13px;
    color: #92400e;
    margin-top: 10px;
  }

  .note strong { color: #78350f; }

  /* Tables */
  .table-wrap { overflow-x: auto; margin-top: 8px; }

  table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }

  thead tr { background: #1a1a2e; color: white; }
  thead th { padding: 10px 16px; text-align: left; font-weight: 600; font-size: 12px; text-transform: uppercase; letter-spacing: 0.5px; }

  tbody tr:nth-child(even) { background: #f7fafc; }
  tbody tr:nth-child(odd)  { background: white; }
  tbody tr:hover { background: #ebf8ff; }

  td { padding: 10px 16px; border-bottom: 1px solid #e2e8f0; color: #2d3748; }

  td:first-child { font-weight: 600; color: #1a1a2e; }

  .yes { color: #27ae60; font-weight: 700; }
  .no  { color: #e94560; font-weight: 700; }

  /* Reference section */
  .ref-section {
    background: white;
    border-radius: 10px;
    padding: 24px;
    margin-top: 32px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.07);
  }

  .ref-section h2 {
    font-size: 16px;
    font-weight: 700;
    color: #1a1a2e;
    margin-bottom: 14px;
    padding-bottom: 10px;
    border-bottom: 2px solid #f0f2f5;
  }

  footer {
    text-align: center;
    padding: 24px;
    font-size: 12px;
    color: #a0aec0;
  }
</style>
</head>
<body>

<header>
  <h1>Laravel EC2 Deployment Guide</h1>
  <p>AWS EC2 · Ubuntu 26 LTS · Nginx + PHP-FPM + MySQL</p>
  <div>
    <span class="badge badge-nginx">Nginx</span>
    <span class="badge badge-php">PHP 8.5</span>
    <span class="badge badge-mysql">MySQL 8.4</span>
    <span class="badge badge-ubuntu">Ubuntu 26</span>
  </div>
</header>

<div class="container">

  <!-- PART 1 -->
  <div class="part-header">
    <span class="part-label">Part 1</span>
    <span class="part-title">Every Laravel Deployment</span>
  </div>
  <p class="part-desc">These steps are required regardless of which Laravel project you are deploying. Do this every time on a fresh server.</p>

  <!-- Step 1 -->
  <div class="step">
    <div class="step-header">
      <div class="step-num">1</div>
      <div class="step-title">Update System</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-sudo">sudo</span> <span class="cmd-default">apt update &&</span> <span class="cmd-sudo">sudo</span> <span class="cmd-default">apt upgrade</span> <span class="cmd-flag">-y</span></pre>
    </div>
  </div>

  <!-- Step 2 -->
  <div class="step">
    <div class="step-header">
      <div class="step-num">2</div>
      <div class="step-title">Install Nginx — Web Server</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-sudo">sudo</span> <span class="cmd-default">apt install nginx</span> <span class="cmd-flag">-y</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl start nginx</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl enable nginx</span></pre>
    </div>
  </div>

  <!-- Step 3 -->
  <div class="step">
    <div class="step-header">
      <div class="step-num">3</div>
      <div class="step-title">Install PHP + Required Extensions</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-comment"># Check available PHP version first</span>
<span class="cmd-default">apt-cache show php | grep Version</span>

<span class="cmd-comment"># Install PHP and all extensions Laravel needs</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">apt install php php-cli php-mbstring php-xml php-bcmath \
php-curl php-zip php-mysql php-tokenizer unzip</span> <span class="cmd-flag">-y</span>

<span class="cmd-comment"># Verify</span>
<span class="cmd-php">php</span> <span class="cmd-flag">-v</span></pre>
    </div>
  </div>

  <!-- Step 4 -->
  <div class="step">
    <div class="step-header">
      <div class="step-num">4</div>
      <div class="step-title">Install PHP-FPM — Connects PHP to Nginx</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-comment"># Replace 8.5 with your actual PHP version from Step 3</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">apt install php8.5-fpm</span> <span class="cmd-flag">-y</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl start php8.5-fpm</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl enable php8.5-fpm</span></pre>
    </div>
  </div>

  <!-- Step 5 -->
  <div class="step">
    <div class="step-header">
      <div class="step-num">5</div>
      <div class="step-title">Install Composer — PHP Package Manager</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-default">curl -sS https://getcomposer.org/installer |</span> <span class="cmd-php">php</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">mv composer.phar /usr/local/bin/composer</span>

<span class="cmd-comment"># Verify</span>
<span class="cmd-composer">composer</span> <span class="cmd-flag">--version</span></pre>
    </div>
  </div>

  <!-- Step 6 -->
  <div class="step">
    <div class="step-header">
      <div class="step-num">6</div>
      <div class="step-title">Install Node.js + npm — Frontend Assets</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-default">curl -fsSL https://deb.nodesource.com/setup_18.x |</span> <span class="cmd-sudo">sudo</span> <span class="cmd-flag">-E</span> <span class="cmd-default">bash -</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">apt install</span> <span class="cmd-flag">-y</span> <span class="cmd-default">nodejs</span>

<span class="cmd-comment"># Verify</span>
<span class="cmd-default">node</span> <span class="cmd-flag">-v</span> <span class="cmd-default">&& npm</span> <span class="cmd-flag">-v</span></pre>
    </div>
  </div>

  <!-- Step 7 -->
  <div class="step">
    <div class="step-header">
      <div class="step-num">7</div>
      <div class="step-title">Install MySQL — Database</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-sudo">sudo</span> <span class="cmd-default">apt install mysql-server</span> <span class="cmd-flag">-y</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl start mysql</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl enable mysql</span>

<span class="cmd-comment"># Verify</span>
<span class="cmd-default">mysql</span> <span class="cmd-flag">--version</span></pre>
    </div>
  </div>

  <!-- PART 2 -->
  <div class="part-header" style="margin-top:48px;">
    <span class="part-label part2">Part 2</span>
    <span class="part-title">Project Specific — Laracoffee</span>
  </div>
  <p class="part-desc">These steps are specific to this project. Database name, username, password and repo URL will change per project.</p>

  <!-- Step 8 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">8</div>
      <div class="step-title">Create Database and User</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-sudo">sudo</span> <span class="cmd-default">mysql</span></pre>
      <div class="code-label" style="margin-top:12px;">inside mysql shell</div>
      <pre><span class="cmd-mysql">CREATE DATABASE</span> <span class="cmd-default">laracoffee;</span>
<span class="cmd-mysql">CREATE USER</span> <span class="cmd-val">'larauser'</span><span class="cmd-default">@</span><span class="cmd-val">'localhost'</span> <span class="cmd-mysql">IDENTIFIED BY</span> <span class="cmd-val">'Laravel@123'</span><span class="cmd-default">;</span>
<span class="cmd-mysql">GRANT ALL PRIVILEGES ON</span> <span class="cmd-default">laracoffee.*</span> <span class="cmd-mysql">TO</span> <span class="cmd-val">'larauser'</span><span class="cmd-default">@</span><span class="cmd-val">'localhost'</span><span class="cmd-default">;</span>
<span class="cmd-mysql">FLUSH PRIVILEGES;</span>
<span class="cmd-mysql">EXIT;</span></pre>
    </div>
  </div>

  <!-- Step 9 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">9</div>
      <div class="step-title">Clone the Repository</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-default">cd /root</span>
<span class="cmd-git">git</span> <span class="cmd-default">clone https://github.com/snykk/Laracoffee.git</span>
<span class="cmd-default">cd Laracoffee</span></pre>
    </div>
  </div>

  <!-- Step 10 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">10</div>
      <div class="step-title">Install PHP Dependencies</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-composer">composer</span> <span class="cmd-default">install</span></pre>
    </div>
  </div>

  <!-- Step 11 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">11</div>
      <div class="step-title">Install Node Dependencies</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-npm">npm</span> <span class="cmd-default">install</span></pre>
    </div>
  </div>

  <!-- Step 12 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">12</div>
      <div class="step-title">Configure Environment File</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-default">cp .env.example .env</span>
<span class="cmd-default">nano .env</span></pre>
      <div class="code-label" style="margin-top:12px;">update these values inside .env</div>
      <pre><span class="cmd-key">DB_DATABASE</span><span class="cmd-default">=</span><span class="cmd-val">laracoffee</span>
<span class="cmd-key">DB_USERNAME</span><span class="cmd-default">=</span><span class="cmd-val">larauser</span>
<span class="cmd-key">DB_PASSWORD</span><span class="cmd-default">=</span><span class="cmd-val">Laravel@123</span></pre>
      <div class="note">Save with <strong>Ctrl+X → Y → Enter</strong></div>
    </div>
  </div>

  <!-- Step 13 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">13</div>
      <div class="step-title">Generate App Key</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-php">php</span> <span class="cmd-default">artisan key:generate</span></pre>
    </div>
  </div>

  <!-- Step 14 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">14</div>
      <div class="step-title">Create Storage Symlink</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-php">php</span> <span class="cmd-default">artisan storage:link</span></pre>
    </div>
  </div>

  <!-- Step 15 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">15</div>
      <div class="step-title">Run Migrations and Seeders</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-php">php</span> <span class="cmd-default">artisan migrate</span>
<span class="cmd-php">php</span> <span class="cmd-default">artisan db:seed</span></pre>
    </div>
  </div>

  <!-- Step 16 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">16</div>
      <div class="step-title">Set File Permissions</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-default">chmod</span> <span class="cmd-flag">-R</span> <span class="cmd-default">755 /root</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">chown</span> <span class="cmd-flag">-R</span> <span class="cmd-default">www-data:www-data /root/Laracoffee/storage</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">chown</span> <span class="cmd-flag">-R</span> <span class="cmd-default">www-data:www-data /root/Laracoffee/bootstrap/cache</span></pre>
    </div>
  </div>

  <!-- Step 17 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">17</div>
      <div class="step-title">Configure Nginx</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-sudo">sudo</span> <span class="cmd-default">nano /etc/nginx/sites-available/laracoffee</span></pre>
      <div class="code-label" style="margin-top:12px;">paste this nginx config</div>
      <pre><span class="cmd-key">server</span> <span class="cmd-default">{</span>
    <span class="cmd-key">listen</span> <span class="cmd-val">80</span><span class="cmd-default">;</span>
    <span class="cmd-key">server_name</span> <span class="cmd-val">_</span><span class="cmd-default">;</span>
    <span class="cmd-key">root</span> <span class="cmd-val">/root/Laracoffee/public</span><span class="cmd-default">;</span>

    <span class="cmd-key">add_header</span> <span class="cmd-default">X-Frame-Options</span> <span class="cmd-val">"SAMEORIGIN"</span><span class="cmd-default">;</span>
    <span class="cmd-key">add_header</span> <span class="cmd-default">X-Content-Type-Options</span> <span class="cmd-val">"nosniff"</span><span class="cmd-default">;</span>

    <span class="cmd-key">index</span> <span class="cmd-default">index.php;</span>

    <span class="cmd-key">location</span> <span class="cmd-default">/ {</span>
        <span class="cmd-key">try_files</span> <span class="cmd-default">$uri $uri/ /index.php?$query_string;</span>
    <span class="cmd-default">}</span>

    <span class="cmd-key">location</span> <span class="cmd-default">~ \.php$ {</span>
        <span class="cmd-key">fastcgi_pass</span> <span class="cmd-val">unix:/var/run/php/php8.5-fpm.sock</span><span class="cmd-default">;</span>
        <span class="cmd-key">fastcgi_param</span> <span class="cmd-default">SCRIPT_FILENAME $realpath_root$fastcgi_script_name;</span>
        <span class="cmd-key">include</span> <span class="cmd-default">fastcgi_params;</span>
    <span class="cmd-default">}</span>

    <span class="cmd-key">location</span> <span class="cmd-default">~ /\.(?!well-known).* {</span>
        <span class="cmd-key">deny</span> <span class="cmd-default">all;</span>
    <span class="cmd-default">}</span>
<span class="cmd-default">}</span></pre>
      <div class="note">Save with <strong>Ctrl+X → Y → Enter</strong></div>
    </div>
  </div>

  <!-- Step 18 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">18</div>
      <div class="step-title">Enable Site and Restart Nginx</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-comment"># Enable the site</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">ln -s /etc/nginx/sites-available/laracoffee /etc/nginx/sites-enabled/</span>

<span class="cmd-comment"># Remove default site to avoid port 80 conflict</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">rm /etc/nginx/sites-enabled/default</span>

<span class="cmd-comment"># If Apache is running and blocking port 80, stop it</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl stop apache2</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl disable apache2</span>

<span class="cmd-comment"># Test Nginx config</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">nginx -t</span>

<span class="cmd-comment"># Restart services</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl restart nginx</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl restart php8.5-fpm</span></pre>
    </div>
  </div>

  <!-- Step 19 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">19</div>
      <div class="step-title">Verify All Services are Running</div>
    </div>
    <div class="step-body">
      <div class="code-label">bash</div>
      <pre><span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl is-enabled nginx</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl is-enabled php8.5-fpm</span>
<span class="cmd-sudo">sudo</span> <span class="cmd-default">systemctl is-enabled mysql</span></pre>
      <div class="note">All three should return: <strong>enabled</strong></div>
    </div>
  </div>

  <!-- Step 20 -->
  <div class="step project">
    <div class="step-header">
      <div class="step-num">20</div>
      <div class="step-title">Access the App</div>
    </div>
    <div class="step-body">
      <div class="code-label">browser</div>
      <pre><span class="cmd-val">http://&lt;your-ec2-public-ip&gt;</span></pre>
      <div class="note" style="margin-top:10px;">
        No port number needed. Port 80 is default HTTP.<br><br>
        <strong>Admin login (seeded):</strong><br>
        Email: najibfikri13@gmail.com &nbsp;|&nbsp; Password: 1234
      </div>
    </div>
  </div>

  <!-- Quick Reference Table -->
  <div class="ref-section">
    <h2>Quick Reference — What Each Tool Does</h2>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Tool</th>
            <th>Job</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Nginx</td><td>Web server — receives browser requests on port 80</td></tr>
          <tr><td>PHP-FPM</td><td>Processes PHP files — connected to Nginx via Unix socket</td></tr>
          <tr><td>PHP Extensions</td><td>Libraries Laravel needs to run (database, encryption, XML etc.)</td></tr>
          <tr><td>Composer</td><td>PHP package manager — installs Laravel dependencies from composer.json</td></tr>
          <tr><td>Node.js + npm</td><td>Installs frontend dependencies — builds CSS/JS assets via Vite</td></tr>
          <tr><td>MySQL</td><td>Database — stores users, products, orders</td></tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- Comparison Table -->
  <div class="ref-section" style="margin-top:16px;">
    <h2>php artisan serve vs Nginx + PHP-FPM</h2>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th></th>
            <th>php artisan serve</th>
            <th>Nginx + PHP-FPM</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Use for</td><td>Quick local testing only</td><td>Actual deployment</td></tr>
          <tr><td>Survives terminal close</td><td><span class="no">No</span></td><td><span class="yes">Yes</span></td></tr>
          <tr><td>Survives reboot</td><td><span class="no">No</span></td><td><span class="yes">Yes</span></td></tr>
          <tr><td>Can handle real traffic</td><td><span class="no">No</span></td><td><span class="yes">Yes</span></td></tr>
          <tr><td>Interview acceptable</td><td><span class="no">No</span></td><td><span class="yes">Yes</span></td></tr>
        </tbody>
      </table>
    </div>
    <div class="note" style="margin-top:14px;">
      <strong>Remember:</strong> <code>php artisan serve</code> is only used as a sanity check to confirm the app works before setting up the real web server.
    </div>
  </div>

</div>

<footer>Laravel EC2 Deployment Guide · Anushk Dhokne · 2026</footer>

</body>
</html>

 <h1 align="center">Hi 👋, I'm Mob</h1>
<h3 align="center">Join the Cryptocurrency Market, make money from Airdrop - Retroactive with me</h3>

- <p align="left"> <img src="https://komarev.com/ghpvc/?username=mobonchain&label=Profile%20views&color=0e75b6&style=flat" alt="mobonchain" /> <a href="https://github.com/mobonchain"> <img src="https://img.shields.io/github/followers/mobonchain?label=Follow&style=social" alt="Follow" /> </a> </p>

- [![TopAME | Bullish - Cheerful](https://img.shields.io/badge/TopAME%20|%20Bullish-Cheerful-blue?logo=telegram&style=flat)](https://t.me/xTopAME)

# Hướng dẫn cài đặt Dill Node Validator ( LightNode / Full Node )

Hướng dẫn này sẽ giúp bạn cài đặt **LightNode / Full Node Validator** cho dự án **Dill** trên **Alps Testnet**

## Yêu cầu cấu hình VPS tối thiểu :

| **Loại Node** | **CPU** | **Memory** | **Disk** | **Bandwidth** | **OS** |
|---------------|---------|------------|----------|---------------|--------|
| **LightNode**     | 2 Cores | 2 GB RAM   | 20 GB Storage| 8 Mb/s     | Ubuntu LTS 20.04+/MacOS |
| **Full Node**     | 4 Cores | 8 GB RAM   | 256 GB Storage | 64 Mb/s  | Ubuntu LTS 20.04+/MacOS |
- Với **Ubuntu LTS** : cần **CPU** kiến trúc **x86-64** và hỗ trợ tập lệnh **ADX**
  - **Kiểm tra bằng lệnh** : `cat /proc/cpuinfo | grep adx`
  - Nếu kết quả hiển thị có "adx", nghĩa là CPU của bạn đáp ứng yêu cầu 🚀
- Với **macOS** : chỉ hỗ trợ **chip Apple M1/M2**

## Thông tin chuỗi Alps Testnet :
| **Tham Số** | **Giá Trị** |
|-------------|-------------|
| **Tên Mạng** | Alps Testnet |
| **RPC URL** | [https://rpc-alps.dill.xyz](https://rpc-alps.dill.xyz) |
| **ID Chuỗi** | 102125 |
| **Ký Hiệu Tiền Tệ**  | DILL |
| U**RL Trình Khám Phá** | [https://alps.dill.xyz](https://alps.dill.xyz) |

---

## Cài đặt và khởi chạy Dill Node Script ( Step 1 )

- Di chuyển về thư mục người dùng :
```bash 
cd $HOME
```

- Sử dụng `curl` :
```bash
curl -sO https://raw.githubusercontent.com/DillLabs/launch-dill-node/main/dill.sh  && chmod +x dill.sh && ./dill.sh
```

- Hoặc dùng `wget` :
```bash
wget -q https://raw.githubusercontent.com/DillLabs/launch-dill-node/main/dill.sh -O dill.sh && chmod +x dill.sh && ./dill.sh
```
- Sau khi chạy một trong hai lệnh trên và hiện ra thông báo `Step 1 Completed. Press any key to continue...` là hoàn thành
- Nhấn phím bất kỳ để chuyển sang bước tiếp theo

--- 

## Tạo Validator Keys and Password ( Step 2 )

- Đến `Step 2: Generating Validator Keys`
  - Nhập **1** và **Enter** để tạo một `Validator Keys` mới
  - Hoặc nhặp **2** để **Import** lại `Validator Keys` cũ
- Nếu nhập **1** thì đợi quá trình tạo `Validator Keys` và `Password` diễn ra cùng lúc
- Sau khi chạy và hiện ra thông báo cuối cùng `Press any key when you have written down your mnemonic.` là hoàn thành
- Cứ nhấn phím bất kỳ 2 3 lần để chuyển sang bước tiếp theo

---

## Chọn Node và nhập Withdrawal Address ( Thuộc Step 2 )

- Sau khi đã tạo được `Validator Keys` và `Password` sẽ có thông báo yêu cầu như sau:
`Please choose an option for deposit token amount [1, 3600, 2, 36000] [1]:`
- Tùy vào **Cấu hình VPS** và số dư **DILL** bạn đang có để chọn
  - Nhập **1** nếu chạy **LightNode** ( cần 3600 DILL )
  - Nhập **2** nếu chạy **Full Node** ( cần 36000 DILL )
- Sau khi chọn một trong hai option, tiếp theo cần nhập **Withdrawal Address**
`Please enter your withdrawal address:`
  - Dùng bất cứ địa chỉ ví **Metamask** nào bạn muốn ( nhớ là copy từ **Metamask** để tránh gặp lỗi **checksum**), có thể **giống** địa chỉ **Staking** hoặc cũng có thể **Khác**
  - Nhập lại một lần nữa để xác nhận
- Sau khi chạy và hiện ra thông báo cuối cùng `Step 2 Completed. Press any key to continue...` là hoàn thành
- Nhấn phím bất kỳ để chuyển sang bước tiếp theo

---

## Import keys and Start Dill Node ( Step 3 )

- Quá trình này tự động nên chỉ cần xong được **Step 2** thì chỉ cần chờ **Step 3** tự hoàn thành
- hiện ra thông báo cuối cùng `node running, congratulations 😄` là thành công, giờ chỉ việc **Staking**

## Backup thông tin and Staking

- Điều hướng vào thư mục `validator_key` bằng lệnh :
```bash
cd $HOME && cd dill/validator_keys
```
- Gõ `ls` kiểm tra các tệp đang có
  - Nếu chạy đúng sẽ có các tệp như sau : `deposit_data-1739xxxxx.json`, `keystore-m_12xxx_3600_0_0_0-1739xxxxx.json`, `keystore_password.txt` và `mnemonic-1739xxxxx.txt`
  - **⚠️ Tên tệp mỗi người dùng là khác nhau ⚠️**
- Gõ `nano deposit_data-1739xxxxx.json` để lấy thông tin **Staking**
- Copy toàn bộ thông tin `[{"pubkey":.......................deposit_cli_version": "2.7.0"}] 
- Truy cập [https://staking.dill.xyz/en/](https://staking.dill.xyz/en/)
- Dán thông tin vừa **Copy** vào ô `Paste the JSON code here`
- Việc còn lại là tiến hành kết nối ví **có DILL**, xác nhận **Withdrawal Address** rồi **Staking DILL** là xong

❗ Nhớ backup lại các File khác tương tự `nano <name_file>`

## Add thêm Node :
- Nếu đang chạy **Full Node** có thể **Add thêm Full Node** hoặc **LightNode**
- Nếu đang chạy **LightNode** chỉ có thể **Add thêm LightNode**
- **Lệnh Add** : 
```bash
cd $HOME/dill/2_add_validator.sh
```
- Sau đó làm **tương tự** với lúc tạo `Validator Keys`

💡 Tốt nhất là chạy **1 Full Node** & **Add 1 LightNode** sau só **Staking** hết vào **Node**, không cần chạy nhiều Node

🔗 Tìm hiểu thêm tại <a href="https://github.com/DillLabs/launch-dill-node">
  <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="15">
</a> 
**[Dill Labs](https://github.com/DillLabs/launch-dill-node)**

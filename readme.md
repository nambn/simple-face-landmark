Thực hiện lần lượt các bước dưới đây

    0. Cài đặt các thư viện cần thiết

    1. Tải và cài đặt openface

    2. Deploy file service

    3. Deploy faciallandmark service

    4. Chạy react frontend

### Cài đặt thư viện

- dotnet runtime (để chạy 2 service: fileservice và faciallandmark service)
- npm (chạy frontend react)

### deploy openface

- Tải về thư viện openface: https://github.com/TadasBaltrusaitis/OpenFace/releases/download/OpenFace_2.2.0/OpenFace_2.2.0_win_x64.zip

- giải nén và truy cập vào thư mục, chạy file download_models.ps1 để tải models
(cách chạy: mở powershell, cd đến thư mục rồi chạy lệnh bên dưới)

    .\download_models.ps1

- trong thư mục sẽ có 1 file FaceLandmarkImg.exe, ghi nhớ đường dẫn đến file này.

### deploy backend

deploy file service

    - mở 1 terminal
    - cd đến net5.0-fileservice
    - run

        dotnet .\Myrmica.MicroServices.FileStorageService.dll --urls="http://localhost:6000;https://localhost:6001"
        
deploy faciallandmark service

    - mở 1 terminal khác
    - cd đến net5.0-faciallandmarkservice
    - mở file appsettings.json và sửa giá trị của key OpenFaceExe thành đường dẫn đến FaceLandmarkImg.exe
    - đóng file và run

        dotnet .\Myrmica.MicroServices.FacialLandmarkService.dll --urls="http://localhost:7000;https://localhost:7001"


### deploy frontend

- mở 1 terminal khác
- cd đến \frontend
- run

    npm install -g serve
    npx serve
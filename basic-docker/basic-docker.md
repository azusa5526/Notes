# Dockerfile

FROM 指的是一個**階段**，每個 FROM 之下的指令稱為 Layer

Layer 的順序與變更，會影響到 Docker 的快取，影響構建空間與效能

ARG 指的是參數，放置於 FROM 內部

## 多階段構建

使用多階段構建有以下兩種好處

+ 並行構建

    構建階段之間若無順序可使用，增加構建效率，例如 client/server 並行構建。

+ 減少最終 Image 占用大小
    
    只包裝 Build 出來的 Prod code，而不需要整陀構建階段所需要的 node_modules，構建與執行使用不同的 Base image。

## 建構目標 Build targets

可以使用單一一個 dockerfile 建例出多個 Image，例如用一份 dockerfile 建構出 client/server 為不同的 Image

## 掛載 Mounts

掛載分為快取掛載與綁定掛載

+ 快取掛載 (Cache Mounts)

    指定建置的時候，快取要使用的持久性套件，來加速構建速度。
    使用 RUN 指令與 --mount=type=cache,target=<path> 標誌

+ 綁定掛載 (Bind Mounts)

    原先都是使用 COPY 的指令複製本機資源到 container 的檔案目錄裡面，例如 package.json 等，使用綁定掛載可以直接將本機資源直接掛載到 container。
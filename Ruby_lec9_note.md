#[Heroku 雲端上架]
[前言小知識]
dropbox建立在Amazon3
放到雲端上大部分是用linux
DevOps職位：專門維護app能正常運作，公司如果沒有此通常都會落到後端(rails)工程師身上

#[heroku雲端服務]
PaaS (Platform as a Service 即時平台服務)
Rails 界最有名的 Paas 就是 Heroku
Amazon雲端服務相當麻煩
Heroku相當簡單，只要會用git
第一個能夠部署rails app

heroku password:****e2d3
heroku使用postGrass


Gemfile的group :development do
只有開發會安裝，正式環境不會安裝
ex 除錯的Gem、sqllite
每次傳到heroku都一定要commit
在做commit時要像童子軍，經過觀光景點時會撿垃圾，而不要當觀光客
=>讓

git commit --amend
esc 退出編輯模式
:wq寫入然後退出

#[把程式丟到雲端上]
先創造一個 heroku app...
記住，heroku create 一個專案只需做一次，不然會在 heroku 上創出另一個 app
#heroku create
把程式碼推上 heroku..
#git push heroku master
跑 heroku 那邊的db
#heroku run rake db:migrate
用 browser 打開 app
heroku open

feature(平行宇宙)跟master(正式)
heroku只接受master

每一次要更新heroku資料都要進行git的commit
git add .
git status
git commit -m""
git push heroku master

把seed file檔案放到heroku
heroku run rake db:seed

#[Asset Pipeline]
靜態資源：不會因為使用者做事情而變更
避免網頁下載這些靜態資源而花費太多時間=>包成單一檔案(只要下載一次)
壓縮並打包application.js和application.css














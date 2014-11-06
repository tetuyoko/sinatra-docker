# pythonイメージtag2.7をdockerhubから取得
FROM python:2.7

# カレントディレクトリをvmの/codeとしてマウント
ADD . /code

# ワーキングディレクトリを/codeに設定
WORKDIR /code

# pythonライブラリをインストール
RUN pip install -r requirements.txt

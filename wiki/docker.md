## docker 설치하기
# 1. 패키지 업데이트
sudo apt update

# 2. 필수 패키지 설치
// https를 통한 리포지토리 접근을 위한 필수 패키지 설치
sudo apt install apt-transport-https ca-certificates curl software-properties-common

# 3. Docker GPG 키 추가
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker.gpg

# 4. Docker 저장소 추가
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 5. Docker 설치
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

# 6. Docker 실행 권한 부여 (재부팅 또는 재로그인 필요)
sudo usermod -aG docker $USER

# 7. Docker 설치 확인
docker --version
docker compose version
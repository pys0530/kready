# kready

## Rocky Linux 9.5 기준
## Kubeadm으로 쿠버네티스 클러스터 배포하는 과정 중 업데이트, 초기화 과정을 Ansible로 자동화하는 것을 목표로 함.

## 가능하다면  kubeadm init을  --skip-phases=addon/kube-proxy 와 함께 사용하여
## Cilium이 Strict 모드로 kube-proxy를 대체하도록 하는 설정도 Ansible 로 만들도록 할 예정

## Ansible로 만들 과정과 순서는 아래와 같음
1. 업데이트, 노드 초기화(disable swap, firewalld), 필수 패키지 설치 및 helm 설치 - 미완성
2. 커널 모듈 활성화(overlay, br_netfilter) - 미완성
3. /etc/hosts 에 클러스터에 포함된 모든 노드들을 추가 - 미완성
4. init 한 마스터1 에서 나오는 인증서 다른 마스터 노드, 워커노드들에 복사 - 미완성
5. kubernetes repo 추가 및 kubectl kubeadm kubelet 설치 - 미완성
6. 마스터 노드, 워커 노드들 모두 Join - 미완성
7. Helm으로 Cilium 설치 - 미완성

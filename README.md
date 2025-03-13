# kready v0.11

## Introduction
kready는 kubeadm을 활용한 기본적인 Kubernetes 클러스터 배포를 위한 툴로서 아래 툴들로 이루어져있습니다.
- Kubernetes v1.32
- Cilium
- CRI-O

## How works
Ansible을 통한 배포를 기본으로 하며 클러스터에 따라 수정되어야 하는 파일들의 목록은 아래와 같습니다.
- hosts :
  Kubernetes 클러스터들의 모든 노드의 /etc/hosts 에 포함될 내용
- inventory.ini :
  Kubernetes 클러스터에 포함될 모든 노드들의 IP 정보 및 Hostname
- group_vars/kubeadm-vars.yml : 
  kubeadm으로 들어가는 옵션들에 포함될 정보(POD/Service CIDR, Endpoint IP 등)

Haproxy / Keepalived를 통한 Kubeadm HA 및 Haproxy HA 구성
- Master Node(3대 기준)으로 1대가 장애 발생하더라도 클러스터가 문제 없이 작동하게끔 설정
- haproxy/haproxy.cfg -> Haproxy 마스터, Haproxy 백업 서버 모두 등록
- keepalived/keepalived.conf.master -> Keepalived 마스터 서버에 keepalived.conf 로 이름 변경하여 저장
- keepalived/keepalived.conf.backup -> Keepalived 백업 서버에 keepalived.conf 로 이름 변경하여 저장

## Clone
- git clone https://github.com/pys0530/kready.git

## Deploy Command
- (kready 경로에서)
- ansible-playbook -i inventory.ini playbook.yml -b --become-user=root

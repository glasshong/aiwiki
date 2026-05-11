# 효율적 Attention

기본 Self-Attention은 모든 token 쌍을 비교합니다. Sequence가 길어질수록 계산량과 메모리 사용량이 빠르게 증가합니다.

## Sliding Window Attention

각 token이 주변 window 안의 token만 참고합니다.

## Local Attention

각 token이 가까운 주변 token만 참고하도록 제한합니다.

## Global Attention

특정 token이 전체 sequence를 볼 수 있게 하거나, 모든 token이 전체 sequence를 보는 방식입니다.

## Flash Attention

Attention 수식을 근사하지 않고 정확히 계산하되, GPU 메모리 읽기/쓰기 비용을 줄이도록 구현한 알고리즘입니다.

참고: [FlashAttention](https://arxiv.org/abs/2205.14135)

# LP-LRU
RocksDB의 Bloom filter 코스트를 고려/반영한 캐시 정책
※현재 독립적인 캐시를 구현한 것이 아니라 존재하는 기능을 변형하여 구현함

## 참고 자료
RocksDB 관련 정보: [RocksDB](ㅊ)  
블룸 필터 Hashing cost: ["Reducing Bloom filter CPU Overhead in LSM-Trees on Modern Storage Devices", Zichen Zhu, DAMON 21](https://dl.acm.org/doi/abs/10.1145/3465998.3466002)

## 구현 내용
table/block_based의 block_based_table_reader.cc 파일을 수정
기존 RocksDB는 index와 filter와 관련된 block을 따로 cache에 저장하는 기능을 지원함.
또한, index와 filter block이 data block 보다 많아지는 것을 제한하기 위해 캐시 비율을 할당해줌.
이를 변경하여 LSM-tree의 각 레벨에 우선순위를 부여하고, 우선 순위에 따라 캐시 관리가 이루어지도록 구현함

## 캐시 동작

## 실험 내용

## 실험 결과

## 개선할 점
cache/lru_cache.cc 처럼 독립된 캐시로 구현해야함
현재 작은 성능 변화를 향상시켜야함

<template>
  <div class="fourth">
    <div id="map" style="width:100%;height:30%"></div>
    <table>
      <tr>
        <td class="title">일시</td>
        <td>2018년 9월 1일 토요일 낮 12시</td>
      </tr>
      <tr>
        <td class="title">주소</td>
        <td>서울시 구로구 경인로 610 (신도림동 413-9) 신도림 S컨벤션웨딩홀</td>
      </tr>
      <tr>
        <td class="title">지하철</td>
        <td>1호선 구로역 3번 출구 우측방향 도보 5분 1, 2호선 신도림역 1번 출구 좌측방향 도보 7분</td>
      </tr>
      <tr>
        <td class="title">셔틀버스</td>
        <td>1, 2호선 신도림역 1번출구 디큐브시티 앞</td>
      </tr>
      <tr>
        <td class="title">문의</td>
        <td>02-2652-3000</td>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  name: 'Map',
  mounted() {
    const center = new window.naver.maps.LatLng(37.505485, 126.883925);
    const map = new window.naver.maps.Map('map', {
      center,
      zoom: 10,
      scaleControl: false,
      logoControl: false,
      mapDataControl: false,
      mapTypeControl: false,
      zoomControl: true,
      zoomControlOptions: {
        style: window.naver.maps.ZoomControlStyle.SMALL,
        position: window.naver.maps.Position.RIGHT_TOP,
      },
    });

    const mapElement = map.getElement();
    window.naver.maps.Event.addDOMListener(mapElement, 'touchstart', (e) => {
      e.stopPropagation();
    });
  },
};
</script>


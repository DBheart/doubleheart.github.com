## [맛보기](https://wkdtjsgur100.github.io/react=jest/)
툴은 VS code사용
create-react-app으로 프로젝트 생성
테스트대상과 테스트파일 생성(아래 참조)
CLI에서 “npm test” or “yarn test” 실행
create-react-app에는 이미 jest가 적용되어 있고, test라는 스크립트가 들어가 있다.

sum.js
```
function sum(a, b) {
  return a + b;
}
module.exports = sum;
```

sum.test.js
```
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

---

## [본격적으로 보기](https://velog.io/@velopert/react-testing)
> velopert의 테스트케이서 1~8장을 보는게 더 빠르다. 하지만 보완도 필요할것 같다. 바로 redux사용하는 부분..
>> 현재 프로젝트에서 redux를 사용하였고 store를 썼는데 이부분을 상속으로 처리하였다. 상속받은 store부분을 인식하지 못하여서 테스트케이스를 못하고 있는데, 실제 프로젝트에서는 store를 쓸것이므로 이부분을 어떻게 할지 알아두는것이 제일 시급해 보인다.

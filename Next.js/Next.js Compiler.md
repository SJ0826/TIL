# Next.js Compiler

Next.js의 컴파일러는 Rust로 만든 **SWC**

Next.js의 JS코드를 변환하고 minify하는 역할을 한다.

Babel과 Tersel을 대체한다.

## SWC(Speedy Web Compiler)

babel보다 약 17배, terser보다 약 7배 빠르다.

왜 빠른가?

싱글 스레드 기반의 JS와는 달리 병렬 처리를 고려한 Rust로 만들어졌기 때문이다.

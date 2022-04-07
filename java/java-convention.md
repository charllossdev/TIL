https://programmer-ririhan.tistory.com/338


<body class="book toc2 toc-left">
<div id="header">
  <h1>캠퍼스 핵데이 Java 코딩 컨벤션</h1>
  <div class="details">
    <span id="revnumber">version unspecified</span>
  </div>
  <div id="toc" class="toc2">
    <div id="toctitle">Table of Contents</div>
    <ul class="sectlevel1">
      <li><a href="#_파일_공통_요건">1. 파일 공통 요건</a>
        <ul class="sectlevel2">
          <li><a href="#encoding-utf8">1.1. 파일 인코딩은 UTF-8</a></li>
          <li><a href="#newline-lf">1.2. 새줄 문자는 LF</a></li>
          <li><a href="#newline-eof">1.3. 파일의 마지막에는 새줄</a></li>
        </ul>
      </li>
      <li><a href="#naming">2. 이름 (Naming)</a>
        <ul class="sectlevel2">
          <li><a href="#identifier-char-scope">2.1. 식별자에는 영문/숫자/언더스코어만 허용</a></li>
          <li><a href="#avoid-korean-pronounce">2.2. 한국어 발음대로의 표기 금지</a></li>
          <li><a href="#list-uppercase-abbr">2.3. 대문자로 표기할 약어 명시</a></li>
          <li><a href="#package-lowercase">2.4. 패키지 이름은 소문자로 구성</a></li>
          <li><a href="#class-interface-lower-camelcase">2.5. 클래스/인터페이스 이름에 대문자 카멜표기법 적용</a></li>
          <li><a href="#class-noun">2.6. 클래스 이름에 명사 사용</a></li>
          <li><a href="#interface-noun-adj">2.7. 인터페이스 이름에 명사/형용사 사용</a></li>
          <li><a href="#test-class-suffix">2.8. 테스트 클래스는 'Test’로 끝남</a></li>
          <li><a href="#method-lower-camelcase">2.9. 메서드 이름에 소문자 카멜표기법 적용</a></li>
          <li><a href="#method-verb-preposition">2.10. 메서드 이름은 동사/전치사로 시작</a></li>
          <li><a href="#constant_uppercase">2.11. 상수는 대문자와 언더스코어로 구성</a></li>
          <li><a href="#var-lower-camelcase">2.12. 변수에 소문자 카멜표기법 적용</a></li>
          <li><a href="#avoid-1-char-var">2.13. 임시 변수 외에는 1 글자 이름 사용 금지</a></li>
        </ul>
      </li>
      <li><a href="#declarations">3. 선언 (Declarations)</a>
        <ul class="sectlevel2">
          <li><a href="#1-top-level-class">3.1. 소스파일당 1개의 탑레벨 클래스를 담기</a></li>
          <li><a href="#avoid-star-import">3.2. static import에만 와일드 카드 허용</a></li>
          <li><a href="#modifier-order">3.3. 제한자 선언의 순서</a></li>
          <li><a href="#newline-after-annotation">3.4. 애너테이션 선언 후 새줄 사용</a></li>
          <li><a href="#1-state-per-line">3.5. 한 줄에 한 문장</a></li>
          <li><a href="#1-var-per-declaration">3.6. 하나의 선언문에는 하나의 변수만</a></li>
          <li><a href="#array-square-after-type">3.7. 배열에서 대괄호는 타입 뒤에 선언</a></li>
          <li><a href="#long-value-suffix">3.8. `long`형 값의 마지막에 `L`붙이기</a></li>
          <li><a href="#special-escape">3.9. 특수 문자의 전용 선언 방식을 활용</a></li>
        </ul>
      </li>
      <li><a href="#indentation">4. 들여쓰기 (Indentation)</a>
        <ul class="sectlevel2">
          <li><a href="#indentation-tab">4.1. 하드탭 사용</a></li>
          <li><a href="#4-spaces-tab">4.2. 탭의 크기는 4개의 스페이스</a></li>
          <li><a href="#block-indentation">4.3. 블럭 들여쓰기</a></li>
        </ul>
      </li>
      <li><a href="#braces">5. 중괄호 (Braces)</a>
        <ul class="sectlevel2">
          <li><a href="#braces-knr-style">5.1. K&amp;R 스타일로 중괄호 선언</a></li>
          <li><a href="#sub-flow-after-brace">5.2. 닫는 중괄호와 같은 줄에 <code>else</code>, <code>catch</code>, <code>finally</code>, <code>while</code> 선언</a></li>
          <li><a href="#permit-concise-empty-block">5.3. 빈 블럭에 새줄 없이 중괄호 닫기 허용</a></li>
          <li><a href="#need-braces">5.4. 조건/반복문에 중괄호 필수 사용</a></li>
        </ul>
      </li>
      <li><a href="#line-wrapping">6. 줄바꿈 (Line-wrapping)</a>
        <ul class="sectlevel2">
          <li><a href="#line-length-120">6.1. 최대 줄 너비는 120</a></li>
          <li><a href="#1-line-package-import">6.2. <code>package</code>,<code>import</code> 선언문은 한 줄로</a></li>
          <li><a href="#indentation-after-line-wrapping">6.3. 줄바꿈 후 추가 들여쓰기</a></li>
          <li><a href="#line-wrapping-position">6.4. 줄바꿈 허용 위치</a></li>
        </ul>
      </li>
      <li><a href="#blank-lines)">7. 빈 줄(Blank lines)</a>
        <ul class="sectlevel2">
          <li><a href="#blankline-after-package">7.1. <code>package</code> 선언 후 빈 줄 삽입</a></li>
          <li><a href="#import-grouping">7.2. <code>import</code> 선언의 순서와 빈 줄 삽입</a></li>
          <li><a href="#blankline-between-methods">7.3. 메소드 사이에 빈 줄 삽입</a></li>
        </ul>
      </li>
      <li><a href="#_공백_whitespace">8. 공백 (Whitespace)</a>
        <ul class="sectlevel2">
          <li><a href="#no-trailing-spaces">8.1. 공백으로 줄을 끝내지 않음</a></li>
          <li><a href="#space-after-bracket">8.2. 대괄호 뒤에 공백 삽입</a></li>
          <li><a href="#space-around-brace">8.3. 중괄호의 시작 전, 종료 후에 공백 삽입</a></li>
          <li><a href="#space-between-keyword-parentheses">8.4. 제어문 키워드와 여는 소괄호 사이에 공백 삽입</a></li>
          <li><a href="#no-space-between-identifier-parentheses">8.5. 식별자와 여는 소괄호 사이에 공백 미삽입</a></li>
          <li><a href="#no-space-typecasting">8.6. 타입 캐스팅에 쓰이는 소괄호 내부 공백 미삽입</a></li>
          <li><a href="#generic-whitespace">8.7. 제네릭스 산괄호의 공백 규칙</a></li>
          <li><a href="#space-after-comma-semicolon">8.8. 콤마/구분자 세미콜론의 뒤에만 공백 삽입</a></li>
          <li><a href="#space-around-colon">8.9. 콜론의 앞 뒤에 공백 삽입</a></li>
          <li><a href="#space-around-binary-ternary-operator">8.10. 이항/삼항 연산자의 앞 뒤에 공백 삽입</a></li>
          <li><a href="#no-space-unary-operator">8.11. 단항 연산자와 연산 대상 사이에 공백을 미삽입</a></li>
          <li><a href="#space-around-comment">8.12. 주석문 기호 전후의 공백 삽입</a></li>
        </ul>
      </li>
      <li><a href="#editorconfig">Appendix A: .editorconfig 파일 설정</a></li>
      <li><a href="#checkstyle">Appendix B: Checkstyle 사용법</a>
        <ul class="sectlevel2">
          <li><a href="#checkstyle-version">B.1. 필수 버전</a></li>
          <li><a href="#checkstyle-rule-download">B.2. 규칙 설정 파일 다운로드</a></li>
          <li><a href="#checkstyle-rule-execution">B.3. 검사 실행</a></li>
          <li><a href="#checkstyle-rule-finding">B.4. 관련 규칙 확인 방법</a></li>
          <li><a href="#checkstyle-rule-limitation">B.5. 검사할 수 없는 규칙</a></li>
          <li><a href="#checkstyle-rule-suppressions">B.6. 검사 대상에서 제외하기</a></li>
          <li><a href="#checkstyle-customizing">B.7. 커스터마이징</a></li>
        </ul>
      </li>
      <li><a href="#_빌드_도구_설정">Appendix C: 빌드 도구 설정</a>
        <ul class="sectlevel2">
          <li><a href="#_maven">C.1. Maven</a></li>
          <li><a href="#_gradle">C.2. Gradle</a></li>
        </ul>
      </li>
      <li><a href="#editor-config">Appendix D: 편집기 설정</a>
        <ul class="sectlevel2">
          <li><a href="#_eclipse">D.1. Eclipse</a></li>
          <li><a href="#_intellij">D.2. IntelliJ</a></li>
          <li><a href="#_vi">D.3. VI</a></li>
          <li><a href="#_github">D.4. Github</a></li>
        </ul>
      </li>
    </ul>
  </div>
</div>
<div id="content">
  <div id="preamble">
    <div class="sectionbody">
      <div class="paragraph">
        <p>v1.2.0, 2020.07.24</p>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="_파일_공통_요건">1. 파일 공통 요건</h2>
    <div class="sectionbody">
      <div class="sect2">
        <h3 id="encoding-utf8">1.1. 파일 인코딩은 UTF-8</h3>
        <div class="paragraph">
          <p><em>[encoding-utf8]</em></p>
        </div>
        <div class="paragraph">
          <p>모든 소스, 텍스트 문서 파일의 인코딩은 UTF-8로 통일한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="newline-lf">1.2. 새줄 문자는 LF</h3>
        <div class="paragraph">
          <p><em>[newline-lf]</em></p>
        </div>
        <div class="paragraph">
          <p>Unix 형식의 새줄 문자(newline)인 LF(Line Feed, 0x0A)을 사용한다. Windows 형식인 CRLF가 섞이지 않도록 편집기와 GIT 설정 등을 확인한다.</p>
        </div>
        <div class="paragraph">
          <p>Git을 쓴다면 <code>.gitattribute</code> 파일 안에 정책을 선언해서 지정된 새줄 문자로 강제 변환하거나 예외가 될 확장자를 지정할 수 있다. 아래는 그 예시이다.</p>
        </div>
        <div class="listingblock">
          <div class="content">
<pre class="highlight"><code>*.c text eol=lf
*.cpp text eol=lf
*.h text eol=lf

# exception for visual studio project configuration
*.sln text eol=crlf
*.vs text eol=crlf
*.csproj eol=crlf
*.props eol=crlf
*.filters eol=crlf</code></pre>
          </div>
        </div>
        <div class="paragraph">
          <p><code>.gitattributes</code> 파일은 디렉토리별로 지정할 수 있다. 전체 프로젝트에 적용한다면 최상위 디렉토리에 둔다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="newline-eof">1.3. 파일의 마지막에는 새줄</h3>
        <div class="paragraph">
          <p><em>[newline-eof]</em></p>
        </div>
        <div class="paragraph">
          <p>파일의 마지막은 새줄 문자 LF로 끝나야 한다.</p>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="naming">2. 이름 (Naming)</h2>
    <div class="sectionbody">
      <div class="sect2">
        <h3 id="identifier-char-scope">2.1. 식별자에는 영문/숫자/언더스코어만 허용</h3>
        <div class="paragraph">
          <p><em>[identifier-char-scope]</em></p>
        </div>
        <div class="paragraph">
          <p>변수명, 클래스명, 메서드명 등에는 영어와 숫자만을 사용한다. 상수에는 단어 사이의 구분을 위하여 언더스코어(<code>_</code>)를 사용한다. 정규표현식 `[^A-Za-z0-9_]`에 부합해야 한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="avoid-korean-pronounce">2.2. 한국어 발음대로의 표기 금지</h3>
        <div class="paragraph">
          <p><em>[avoid-korean-pronounce]</em></p>
        </div>
        <div class="paragraph">
          <p>식별자의 이름을 한글 발음을 영어로 옮겨서 표기하지 않는다. 한국어 고유명사는 예외이다.</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p>나쁜 예 : <code>moohyungJasan</code> (무형자산)</p>
            </li>
            <li>
              <p>좋은 예 : <code>intangibleAssets</code> (무형자산)</p>
            </li>
          </ul>
        </div>
      </div>
      <div class="sect2">
        <h3 id="list-uppercase-abbr">2.3. 대문자로 표기할 약어 명시</h3>
        <div class="paragraph">
          <p><em>[list-uppercase-abbr]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스명, 변수명에 쓰일 단어 중 모든 글자를 대문자로 표기할 약어의 목록을 프로젝트별로 명시적으로 정의한다.</p>
        </div>
        <div class="paragraph">
          <p>약어의 대소문자 표기는 JDK의 클래스나 라이브러리들 사이에서도 일관된 규칙이 없다.
            `javax.xml.bind.annotation.XmlElement`처럼 약어를 소문자로 표기하기도 하고, `java.net.HttpURLConnection`처럼 한 클래스 안에서 단어별로 다르게 쓰기도 했다.
            그러나 단일 프로젝트에서는 규칙이 명확하지 않으면 같은 단어의 조합을 다른 이름으로 표기할 수 있어서 혼동을 유발한다.</p>
        </div>
        <div class="paragraph">
          <p>약어가 클래스명에서 대문자로 들어가면 단어 간의 구분을 인지하기에 불리하다. 약어가 연속된 경우 더욱 가독성을 해친다. 예를 들면 XMLRPCHTTPAPIURL과 같은 경우이다.
            그래서 기본 정책으로는 약어의 중간단어를 소문자로 표기하고 프로젝트별로 모두 대문자로 표기할 약어의 목록을 명시하는 방식이 가독성을 높이고 규칙을 단순화하는데 유리하다.
            즉 프로젝트 내에서 정의한 단어 목록이 없다면 'XmlRpcHttpApiUrl’과 같이 쓴다.</p>
        </div>
        <div class="paragraph">
          <div class="title">좋은 예</div>
          <p>HTTP + API + URL 의 클래스 이름의 경우</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p>대문자로 표기할 약어의 목록을 정의하지 않는 경우 : HttpApiUrl</p>
            </li>
            <li>
              <p>API만 대문자로 표기할 약어의 목록에 있을 경우 : HttpAPIUrl</p>
            </li>
            <li>
              <p>HTTP, API, URL이 대문자로 표기할 약어의 목록에 있을 경우 : HTTPAPIURL</p>
            </li>
          </ul>
        </div>
      </div>
      <div class="sect2">
        <h3 id="package-lowercase">2.4. 패키지 이름은 소문자로 구성</h3>
        <div class="paragraph">
          <p><em>[package-lowercase]</em></p>
        </div>
        <div class="paragraph">
          <p>패키지 이름은 소문자를 사용하여 작성한다. 단어별 구문을 위해 언더스코어(<code>_</code>)나 대문자를 섞지 않는다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">package com.navercorp.apiGateway

package com.navercorp.api_gateway</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">package com.navercorp.apigateway</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="class-interface-lower-camelcase">2.5. 클래스/인터페이스 이름에 대문자 카멜표기법 적용</h3>
        <div class="paragraph">
          <p><em>[class-interface-lower-camelcase]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스 이름은 단어의 첫 글자를 대문자로 시작하는 대문자 카멜표기법(Upper camel case)을 사용한다. 파스칼표기법(Pascal case)으로도 불린다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public class reservation

public class Accesstoken</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public class Reservation

public class AccessToken</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="class-noun">2.6. 클래스 이름에 명사 사용</h3>
        <div class="paragraph">
          <p><em>[class-noun]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스 이름은 명사나 명사절로 짓는다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="interface-noun-adj">2.7. 인터페이스 이름에 명사/형용사 사용</h3>
        <div class="paragraph">
          <p><em>[interface-noun-adj]</em></p>
        </div>
        <div class="paragraph">
          <p>인터페이스(interface)의 이름은 클래스 이름은 명사/명사절로 혹은 형용사/형용사절로 짓는다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public interface RowMapper {

public interface AutoClosable {</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="test-class-suffix">2.8. 테스트 클래스는 'Test’로 끝남</h3>
        <div class="paragraph">
          <p><em>[test-class-suffix]</em></p>
        </div>
        <div class="paragraph">
          <p>JUnit 등으로 작성한 테스트 코드를 담은 클래스는 'Test’을 마지막에 붙인다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">public class WatcherTest {</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="method-lower-camelcase">2.9. 메서드 이름에 소문자 카멜표기법 적용</h3>
        <div class="paragraph">
          <p><em>[method-lower-camelcase]</em></p>
        </div>
        <div class="paragraph">
          <p>메서드의 이름에는 첫 번째 단어를 소문자로 작성하고, 이어지는 단어의 첫 글자를 대문자로 작성하는 소문자 카멜표기법(Lower camel case)를 사용한다. 테스트 클래스의 메서드 이름에서는 언더스코어를 허용한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="method-verb-preposition">2.10. 메서드 이름은 동사/전치사로 시작</h3>
        <div class="paragraph">
          <p><em>[method-verb-preposition]</em></p>
        </div>
        <div class="paragraph">
          <p>메서드명은 기본적으로는 동사로 시작한다. 다른 타입으로 전환하는 메서드나 빌더 패턴을 구현한 클래스의 메서드에는 전치사를 쓸 수 있다.</p>
        </div>
        <div class="ulist">
          <div class="title">좋은 예</div>
          <ul>
            <li>
              <p>동사사용 : <code>renderHtml()</code></p>
            </li>
            <li>
              <p>전환메서드의 전치사 : <code>toString()</code></p>
            </li>
            <li>
              <p>Builder 패턴 적용한 클래스의 메서드의 전치사 : <code>withUserId(String id)</code></p>
            </li>
          </ul>
        </div>
      </div>
      <div class="sect2">
        <h3 id="constant_uppercase">2.11. 상수는 대문자와 언더스코어로 구성</h3>
        <div class="paragraph">
          <p><em>[constant_uppercase]</em></p>
        </div>
        <div class="paragraph">
          <p>상태를 가지지 않는 자료형이면서 <code>static final`로 선언되어 있는 필드일 때를 상수로 간주한다. 상수 이름은 대문자로 작성하며, 복합어는 언더스코어(`_</code>)를 사용하여 단어를 구분한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public final int UNLIMITED = -1;
public final String POSTAL_CODE_EXPRESSION = “POST”;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="var-lower-camelcase">2.12. 변수에 소문자 카멜표기법 적용</h3>
        <div class="paragraph">
          <p><em>[var-lower-camelcase]</em></p>
        </div>
        <div class="paragraph">
          <p>상수가 아닌 클래스의 멤버변수/지역변수/메서드 파라미터에는 소문자 카멜표기법(Lower camel case)을 사용한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">private boolean Authorized;
private int AccessToken;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">private boolean authorized;
private int accessToken;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="avoid-1-char-var">2.13. 임시 변수 외에는 1 글자 이름 사용 금지</h3>
        <div class="paragraph">
          <p><em>[avoid-1-char-var]</em></p>
        </div>
        <div class="paragraph">
          <p>메서드 블럭 범위 이상의 생명 주기를 가지는 변수에는 1글자로 된 이름을 쓰지 않는다. 반복문의 인덱스나 람다 표현식의 파라미터 등 짧은 범위의 임시 변수에는 관례적으로  1글자 변수명을 사용할 수 있다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">HtmlParser p = new HtmlParser();</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">HtmlParser parser = new HtmlParser();</code></pre>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="declarations">3. 선언 (Declarations)</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p>클래스, 필드, 메서드, 변수값, import문 등의 소스 구성요소를 선언할 때 고려해야할 규칙이다.</p>
      </div>
      <div class="sect2">
        <h3 id="1-top-level-class">3.1. 소스파일당 1개의 탑레벨 클래스를 담기</h3>
        <div class="paragraph">
          <p><em>[1-top-level-class]</em></p>
        </div>
        <div class="paragraph">
          <p>탑레벨 클래스(Top level class)는 소스 파일에 1개만 존재해야 한다.
            ( 탑레벨 클래스 선언의 컴파일타임 에러 체크에 대해서는 <a href="http://docs.oracle.com/javase/specs/jls/se7/html/jls-7.html#jls-7.6">Java Language Specification 7.6</a> 참조 )</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public class LogParser {
}

class LogType {
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public class LogParser {
    // 굳이 한 파일안에 선언해야 한다면 내부 클래스로 선언
    class LogType {
    }
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="avoid-star-import">3.2. static import에만 와일드 카드 허용</h3>
        <div class="paragraph">
          <p><em>[avoid-star-import]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스를 import할때는 와일드카드(<code>*</code>) 없이 모든 클래스명을 다 쓴다. static import에서는 와일드카드를  허용한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">import java.util.*;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">import java.util.List;
import java.util.ArrayList;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="modifier-order">3.3. 제한자 선언의 순서</h3>
        <div class="paragraph">
          <p><em>[modifier-order]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스/메서드/멤버변수의 제한자는 Java Language Specification에서 명시한 아래의 순서로 쓴다.</p>
        </div>
        <div class="paragraph">
          <p><code>public protected private abstract static final transient volatile synchronized native strictfp</code></p>
        </div>
        <div class="paragraph">
          <p>( <a href="http://docs.oracle.com/javase/specs/jls/se7/html/jls-18.html">Java Language Specification - Chapter 18. Syntax</a> 참조)</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="newline-after-annotation">3.4. 애너테이션 선언 후 새줄 사용</h3>
        <div class="paragraph">
          <p><em>[newline-after-annotation]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스, 인터페이스, 메서드, 생성자에 붙는 애너테이션은 선언 후 새줄을 사용한다. 이 위치에서도 파라미터가 없는 애너테이션 1개는 같은 줄에 선언할 수 있다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">@RequestMapping("/guests")
public void findGuests() {}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">@Override public void destroy() {}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="1-state-per-line">3.5. 한 줄에 한 문장</h3>
        <div class="paragraph">
          <p><em>[1-state-per-line]</em></p>
        </div>
        <div class="paragraph">
          <p>문장이 끝나는 <code>;</code> 뒤에는 새줄을 삽입한다. 한 줄에 여러 문장을 쓰지 않는다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">int base = 0; int weight = 2;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">int base = 0;
int weight = 2;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="1-var-per-declaration">3.6. 하나의 선언문에는 하나의 변수만</h3>
        <div class="paragraph">
          <p><em>[1-var-per-declaration]</em></p>
        </div>
        <div class="paragraph">
          <p>변수 선언문은 한 문장에서 하나의 변수만을 다룬다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">int base, weight;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">int base;
int weight;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="array-square-after-type">3.7. 배열에서 대괄호는 타입 뒤에 선언</h3>
        <div class="paragraph">
          <p><em>[array-square-after-type]</em></p>
        </div>
        <div class="paragraph">
          <p>배열 선언에 오는 대괄호(<code>[]</code>)는 타입의 바로 뒤에 붙인다. 변수명 뒤에 붙이지 않는다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">String names[];</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">String[] names;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="long-value-suffix">3.8. `long`형 값의 마지막에 `L`붙이기</h3>
        <div class="paragraph">
          <p><em>[long-value-suffix]</em></p>
        </div>
        <div class="paragraph">
          <p>long형의 숫자에는 마지막에  대문자 'L’을 붙인다. 소문자 'l’보다 숫자 '1’과의 차이가 커서 가독성이 높아진다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">long base = 54423234211l;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">long base = 54423234211L;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="special-escape">3.9. 특수 문자의 전용 선언 방식을 활용</h3>
        <div class="paragraph">
          <p><em>[special-escape]</em></p>
        </div>
        <div class="paragraph">
          <p><code>\b</code>, <code>\f</code>, <code>\n</code>,<code>\r</code>,<code>\t,  `\"</code>, <code>\\</code> 와 같이 특별히 정의된 선언 방식이 있는 특수 문자가 있다. 이런 문자들은 숫자를 이용한 <code>\008</code> 이나 `\u0008`와 같은 숫자를 넣은 선언보다 전용 방식을 활용한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">System.out.println("---\012---");</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">System.out.println("---\n---");</code></pre>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="indentation">4. 들여쓰기 (Indentation)</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p>들여쓰기는 코드의 계층을 구분하기 위해 추가하는 문자이다.</p>
      </div>
      <div class="sect2">
        <h3 id="indentation-tab">4.1. 하드탭 사용</h3>
        <div class="paragraph">
          <p><em>[indentation-tab]</em></p>
        </div>
        <div class="paragraph">
          <p>탭(tab) 문자를 사용하여 들여쓴다. 탭 대신 스페이스를 사용하지 않는다. 이를 잘 준수하기 위해서 스페이스와 탭을 구별해서 보여주도록 에디터를 설정한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="4-spaces-tab">4.2. 탭의 크기는 4개의 스페이스</h3>
        <div class="paragraph">
          <p><em>[4-spaces-tab]</em></p>
        </div>
        <div class="paragraph">
          <p>1개의 탭의 크기는 스페이스 4개와 같도록 에디터에서 설정한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="block-indentation">4.3. 블럭 들여쓰기</h3>
        <div class="paragraph">
          <p><em>[block-indentation]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스, 메서드, 제어문 등의 코드 블럭이 생길 때마다 1단계를 더 들여쓴다.</p>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="braces">5. 중괄호 (Braces)</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p>중괄호(<code>{</code>,<code>}</code>) 는 클래스, 메서드, 제어문의 블럭을 구분한다.</p>
      </div>
      <div class="sect2">
        <h3 id="braces-knr-style">5.1. K&amp;R 스타일로 중괄호 선언</h3>
        <div class="paragraph">
          <p><em>[braces-knr-style]</em></p>
        </div>
        <div class="paragraph">
          <p>클래스 선언, 메서드 선언, 조건/반복문 등의 코드 블럭을 감싸는 중괄호에 적용되는 규칙이다. 중괄호 선언은 K&amp;R 스타일(Kernighan and Ritchie style)을 따른다. 줄의 마지막에서 시작 중괄호`{`를 쓰고 열고 새줄을 삽입한다. 블럭을 마친후에는 새줄 삽입 후 중괄호를 닫는다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public class SearchConditionParser
{
    public boolean isValidExpression(String exp)
    {

        if (exp == null)
        {
            return false;
        }

        for (char ch : exp.toCharArray())
        {
             ....
        }

        return true;
    }
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public class SearchConditionParser {
    public boolean isValidExpression(String exp) {

        if (exp == null) {
            return false;
        }

        for (char ch : exp.toCharArray()) {
            ....
        }

        return true;
    }
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="sub-flow-after-brace">5.2. 닫는 중괄호와 같은 줄에 <code>else</code>, <code>catch</code>, <code>finally</code>, <code>while</code> 선언</h3>
        <div class="paragraph">
          <p><em>[sub-flow-after-brace]</em></p>
        </div>
        <div class="paragraph">
          <p>아래의 키워드는 닫는 중괄호(<code>}</code>) 와 같은 줄에 쓴다.</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p>else</p>
            </li>
            <li>
              <p>catch, finaly</p>
            </li>
            <li>
              <p>do-while 문에서의 while</p>
            </li>
          </ul>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">if (line.startWith(WARNING_PREFIX)) {
    return LogPattern.WARN;
}
else if (line.startWith(DANGER_PREFIX)) {
    return LogPattern.DANGER;
}
else {
    return LogPattern.NORMAL;
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">if (line.startWith(WARNING_PREFIX)) {
    return LogPattern.WARN;
} else if (line.startWith(DANGER_PREFIX)) {
    return LogPattern.NORMAL;
} else {
    return LogPattern.NORMAL;
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">try {
    writeLog();
}
catch (IOException ioe) {
    reportFailure(ioe);
}
finally {
    writeFooter();
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">try {
    writeLog();
} catch (IOException ioe) {
    reportFailure(ioe);
} finally {
    writeFooter();
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">do {
    write(line);
    line = readLine();
}
while (line != null);</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">do {
    write(line);
    line = readLine();
} while (line != null);</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="permit-concise-empty-block">5.3. 빈 블럭에 새줄 없이 중괄호 닫기 허용</h3>
        <div class="paragraph">
          <p><em>[permit-concise-empty-block]</em></p>
        </div>
        <div class="paragraph">
          <p>내용이 없는 블럭을 선언할 때는 같은 줄에서 중괄호를 닫는 것을 허용한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">public void close() {}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="need-braces">5.4. 조건/반복문에 중괄호 필수 사용</h3>
        <div class="paragraph">
          <p><em>[need-braces]</em></p>
        </div>
        <div class="paragraph">
          <p>조건, 반복문이 한 줄로 끝더라도 중괄호를 활용한다. 이 문서에 언급된 중괄호의 전후의 공백, 제어문 앞 뒤의 새줄 규칙도 함께 고려한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">if (exp == null) return false;

for (char ch : exp.toCharArray()) if (ch == 0) return false;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">if (exp == null) {
    return false;
}

for (char ch : exp.toCharArray()) {

    if (ch == 0) {
        return false;
    }

}</code></pre>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="line-wrapping">6. 줄바꿈 (Line-wrapping)</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p>줄바꿈은 작성한 명령어가 줄 너비를 초과했을 경우 코드 가독성을 위해서 강제로 줄을 바꾸는 것을 말한다.</p>
      </div>
      <div class="sect2">
        <h3 id="line-length-120">6.1. 최대 줄 너비는 120</h3>
        <div class="paragraph">
          <p><em>[line-length-120]</em></p>
        </div>
        <div class="paragraph">
          <p>최대 줄 사용 너비는 120자까지 가능하다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="1-line-package-import">6.2. <code>package</code>,<code>import</code> 선언문은 한 줄로</h3>
        <div class="paragraph">
          <p><em>[1-line-package-import]</em></p>
        </div>
        <div class="paragraph">
          <p><code>package</code>,<code>import</code> 선언문 중간에서는 줄을 바꾸지 않는다. 최대 줄수를 초과하더라도 한 줄로 쓴다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="indentation-after-line-wrapping">6.3. 줄바꿈 후 추가 들여쓰기</h3>
        <div class="paragraph">
          <p><em>[indentation-after-line-wrapping]</em></p>
        </div>
        <div class="paragraph">
          <p>줄바꿈 이후 이어지는 줄에서는 최초 시작한 줄에서보다 적어도 1단계의 들여쓰기를 더 추가한다.
            IDE의 자동 포메팅 기능으로 이를 동일하게 맞추러면 <a href="#editor-config">Appendix C의 각 IDE별 설정</a>을 참고한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">AbstractAggregateRootTest.AggregateRoot proxyAggregateRoot =
        em.getReference(AbstractAggregateRootTest.AggregateRoot.class, aggregateRoot.getId());</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="line-wrapping-position">6.4. 줄바꿈 허용 위치</h3>
        <div class="paragraph">
          <p><em>[line-wrapping-position]</em></p>
        </div>
        <div class="paragraph">
          <p>가독성을 위해 줄을 바꾸는 위치는 다음 중의 하나로 한다.</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p><code>extends</code> 선언 후</p>
            </li>
            <li>
              <p><code>implements</code> 선언 후</p>
            </li>
            <li>
              <p><code>throws</code> 선언 후</p>
            </li>
            <li>
              <p>시작 소괄호(<code>(</code>) 선언 후</p>
            </li>
            <li>
              <p>콤마(<code>,</code>) 후</p>
            </li>
            <li>
              <p><code>.</code> 전</p>
            </li>
            <li>
              <p>연산자 전</p>
              <div class="ulist">
                <ul>
                  <li>
                    <p><code>+</code>, <code>-</code>, <code>*</code>, <code>/</code>, <code>%</code></p>
                  </li>
                  <li>
                    <p><code>==</code>, <code>!=</code>, <code>&gt;=</code>, <code>&gt;</code>,<code>⇐</code>, <code>&lt;</code>, <code>&amp;&amp;</code>, <code>||</code></p>
                  </li>
                  <li>
                    <p><code>&amp;</code>, <code>|</code>, <code>^</code>, <code>&gt;&gt;&gt;</code>, <code>&gt;&gt;</code>, <code>&lt;&lt;</code>, <code>?</code></p>
                  </li>
                  <li>
                    <p><code>instanceof</code></p>
                  </li>
                </ul>
              </div>
            </li>
          </ul>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public boolen isAbnormalAccess (
    User user, AccessLog log) {

    String message = user.getId() + "|" | log.getPrefix()
        + "|" + SUFFIX;
}</code></pre>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="blank-lines)">7. 빈 줄(Blank lines)</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p>빈 줄은 명령문 그룹의 영역을 표시하기 위하여 사용한다.</p>
      </div>
      <div class="sect2">
        <h3 id="blankline-after-package">7.1. <code>package</code> 선언 후 빈 줄 삽입</h3>
        <div class="paragraph">
          <p><em>[blankline-after-package]</em></p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">package com.naver.lucy.util;

import java.util.Date;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="import-grouping">7.2. <code>import</code> 선언의 순서와 빈 줄 삽입</h3>
        <div class="paragraph">
          <p><em>[import-grouping]</em></p>
        </div>
        <div class="paragraph">
          <p>import 구절은 아래와 같은 순서로 그룹을 묶어서 선언한다.</p>
        </div>
        <div class="olist arabic">
          <ol class="arabic">
            <li>
              <p>static imports</p>
            </li>
            <li>
              <p><code>java.</code></p>
            </li>
            <li>
              <p><code>javax.</code></p>
            </li>
            <li>
              <p><code>org.</code></p>
            </li>
            <li>
              <p><code>net.</code></p>
            </li>
            <li>
              <p>8~10을 제외한 <code>com.*</code></p>
            </li>
            <li>
              <p>1~6, 8~10을 제외한 패키지에 있는 클래스</p>
            </li>
            <li>
              <p><code>com.nhncorp.</code></p>
            </li>
            <li>
              <p><code>com.navercorp.</code></p>
            </li>
            <li>
              <p><code>com.naver.</code></p>
            </li>
          </ol>
        </div>
        <div class="paragraph">
          <p>각 그룹 사이에는 빈줄을 삽입한다.
            같은 그룹 내에서는 알파벳 순으로 정렬한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">import java.util.Date;
import java.util.List;

import javax.naming.NamingException;

import org.apache.commons.logging.Log;
import org.apache.commons.logging.LogFactory;
import org.springframework.util.Assert;

import com.google.common.base.Function;

import com.naver.lucy.util.AnnotationUtils;</code></pre>
          </div>
        </div>
        <div class="paragraph">
          <p>이 규칙은 대부분 IDE에서 자동으로 정리해주는 대로 쓰기 때문에 IDE 설정을 일치시키는데 신경을 써야 한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="blankline-between-methods">7.3. 메소드 사이에 빈 줄 삽입</h3>
        <div class="paragraph">
          <p><em>[blankline-between-methods]</em></p>
        </div>
        <div class="paragraph">
          <p>메서드의 선언이 끝난 후 다음 메서드 선언이 시작되기 전에 빈줄을 삽입한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public void setId(int id) {
    this.id = id;
}

public void setName(String name) {
    this.name = name;
}</code></pre>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="_공백_whitespace">8. 공백 (Whitespace)</h2>
    <div class="sectionbody">
      <div class="sect2">
        <h3 id="no-trailing-spaces">8.1. 공백으로 줄을 끝내지 않음</h3>
        <div class="paragraph">
          <p><em>[no-trailing-spaces]</em></p>
        </div>
        <div class="paragraph">
          <p>빈줄을 포함하여 모든 줄은 탭이나 공백으로 끝내지 않는다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="space-after-bracket">8.2. 대괄호 뒤에 공백 삽입</h3>
        <div class="paragraph">
          <p><em>[space-after-bracket]</em></p>
        </div>
        <div class="paragraph">
          <p>닫는 대괄호(<code>]</code>) 뒤에 `;`으로 문장이 끝나지 않고 다른 선언이 올 경우 공백을 삽입한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">int[]masks = new int[]{0, 1, 1};</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">int[] masks = new int[] {0, 1, 1};</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="space-around-brace">8.3. 중괄호의 시작 전, 종료 후에 공백 삽입</h3>
        <div class="paragraph">
          <p><em>[space-around-brace]</em></p>
        </div>
        <div class="paragraph">
          <p>여는 중괄호(<code>{</code>) 앞에는 공백을 삽입한다. 닫는 중괄호(<code>}</code>) 뒤에 <code>else</code> ,<code>catch</code> 등의 키워드가 있을 경우 중괄호와 키워드 사이에 공백을 삽입한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public void printWarnMessage(String line) {
    if (line.startsWith(WARN_PREFIX)) {
        ...
    } else {
        ...
    }
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="space-between-keyword-parentheses">8.4. 제어문 키워드와 여는 소괄호 사이에 공백 삽입</h3>
        <div class="paragraph">
          <p><em>[space-between-keyword-parentheses]</em></p>
        </div>
        <div class="paragraph">
          <p><code>if</code>, <code>for</code>, <code>while</code>, <code>catch</code>, <code>synchronized</code>, <code>switch`와 같은 제어문 키워드의 뒤에 소괄호(</code>(<code>,</code>)`)를 선언하는 경우, 시작 소괄호 앞에 공백을 삽입한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">if (maxLine &gt; LIMITED) {
    return false;
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="no-space-between-identifier-parentheses">8.5. 식별자와 여는 소괄호 사이에 공백 미삽입</h3>
        <div class="paragraph">
          <p><em>[no-space-between-identifier-parentheses]</em></p>
        </div>
        <div class="paragraph">
          <p>식별자와 여는 소괄호(<code>(</code>) 사이에는 공백을 삽입하지 않는다. 생성자와 메서드의 선언, 호출, 애너테이션 선언 뒤에 쓰이는 소괄호가 그에 해당한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public StringProcessor () {} // 생성자

@Cached ("local")
public String removeEndingDot (String original) {
    assertNotNull (original);
    ...
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public StringProcessor() {} // 생성자

@Cached("local")
public String removeEndingDot(String original) {
    assertNotNull(original);
    ...
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="no-space-typecasting">8.6. 타입 캐스팅에 쓰이는 소괄호 내부 공백 미삽입</h3>
        <div class="paragraph">
          <p><em>[no-space-typecasting]</em></p>
        </div>
        <div class="paragraph">
          <p>타입캐스팅을 위해 선언한 소괄호의 내부에는 공백을 삽입하지 않는다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">String message = ( String ) rawLine;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">String message = (String)rawLine;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="generic-whitespace">8.7. 제네릭스 산괄호의 공백 규칙</h3>
        <div class="paragraph">
          <p><em>[generic-whitespace]</em></p>
        </div>
        <div class="paragraph">
          <p>제네릭스(Generics) 선언에 쓰이는 산괄호(<code>&lt;</code>,<code>&gt;</code>) 주위의 공백은 다음과 같이 처리한다.</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p>제네릭스 메서드 선언 일 때만 <code>&lt;</code> 앞에 공백을 삽입한다.</p>
            </li>
            <li>
              <p><code>&lt;</code> 뒤에 공백을 삽입하지 않는다.</p>
            </li>
            <li>
              <p><code>&gt;</code> 앞에 공백을 삽입하지 않는다.</p>
            </li>
            <li>
              <p>아래의 경우를 제외하고는 `&gt;`뒤에 공백을 삽입한다.</p>
              <div class="ulist">
                <ul>
                  <li>
                    <p>메서드 레퍼런스가 바로 이어질 때</p>
                  </li>
                  <li>
                    <p>여는 소괄호('(')가 바로 이어질 때</p>
                  </li>
                  <li>
                    <p>메서드 이름이 바로 이어질 때</p>
                  </li>
                </ul>
              </div>
            </li>
          </ul>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public static &lt;A extends Annotation&gt; A find(AnnotatedElement elem, Class&lt;A&gt; type) { // 제네릭스 메서드 선언
    List&lt;Integer&gt; l1 = new ArrayList&lt;&gt;(); // '(' 가 바로 이어질때
    List&lt;String&gt; l2 = ImmutableList.Builder&lt;String&gt;::new; // 메서드 레퍼런스가 바로 이어질 때
    int diff = Util.&lt;Integer, String&gt;compare(l1, l2); // 메서드 이름이 바로 이어질 때
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="space-after-comma-semicolon">8.8. 콤마/구분자 세미콜론의 뒤에만 공백 삽입</h3>
        <div class="paragraph">
          <p><em>[space-after-comma-semicolon]</em></p>
        </div>
        <div class="paragraph">
          <p>콤마(,)와 반복문(while, for)의 구분자로 쓰이는 세미콜론(<code>;</code>)에는 뒤에만 공백을 삽입한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">for (int i = 0;i &lt; length;i++) {
    display(level,message,i)
}</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">for (int i = 0; i &lt; length; i++) {
    display(level, message, i)
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="space-around-colon">8.9. 콜론의 앞 뒤에 공백 삽입</h3>
        <div class="paragraph">
          <p><em>[space-around-colon]</em></p>
        </div>
        <div class="paragraph">
          <p>반복문과 삼항연산자에서 콜론(<code>:</code>)의 앞 뒤에는 공백을 삽입한다. 라벨 선언 뒤에는 아무런 문자열이 없으므로 앞에만 공백을 삽입한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">for (Customer customer : visitedCustomers) {
    AccessPattern pattern = isAbnormal(accessLog) ? AccessPattern.ABUSE : AccessPattern.NORMAL;
    int grade = evaluate(customer, pattern);

    switch (grade) {
        case GOLD :
            sendSms(customer);
        case SILVER :
            sendEmail(customer);
        default :
            inreasePoint(customer)
    }
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="space-around-binary-ternary-operator">8.10. 이항/삼항 연산자의 앞 뒤에 공백 삽입</h3>
        <div class="paragraph">
          <p><em>[space-around-binary-ternary-operator]</em></p>
        </div>
        <div class="paragraph">
          <p>이항/삼항 연산자의 앞 뒤에는 공백을 삽입한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">if (pattern == Access.ABNORMAL) {
    return 0;
}

finalScore += weight * rawScore - absentCount;

if (finalScore &gt; MAX_LIMIT) {
    return MAX_LIMIT;
}</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="no-space-unary-operator">8.11. 단항 연산자와 연산 대상 사이에 공백을 미삽입</h3>
        <div class="paragraph">
          <p><em>[no-space-increament-decrement-operator]</em></p>
        </div>
        <div class="paragraph">
          <p>단항 연산자와 연산 대상의 사이에는 공백을 삽입하지 않는다.</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p>전위 연산자 : 연산자 뒤에 공백을 삽입하지 않는다.</p>
              <div class="ulist">
                <ul>
                  <li>
                    <p>전위 증감/감소 연산자 : <code>++</code>,<code>--</code></p>
                  </li>
                  <li>
                    <p>부호로 쓰이는 <code>+</code>, <code>-</code></p>
                  </li>
                  <li>
                    <p>NOT 연산자 : <code>~</code>, <code>!</code></p>
                  </li>
                </ul>
              </div>
            </li>
            <li>
              <p>후위 연산자 : 연산자 앞에 공백을 삽입하지 않는다.</p>
              <div class="ulist">
                <ul>
                  <li>
                    <p>후위 증감/감소 연산자 : <code>++</code>,<code>--</code></p>
                  </li>
                </ul>
              </div>
            </li>
          </ul>
        </div>
        <div class="listingblock">
          <div class="title">나쁜 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">int point = score[++ index] * rank -- * - 1;</code></pre>
          </div>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
            <pre class="highlight"><code class="language-java" data-lang="java">int point = score[++index] * rank-- * -1;</code></pre>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="space-around-comment">8.12. 주석문 기호 전후의 공백 삽입</h3>
        <div class="paragraph">
          <p><em>[space-around-comment]</em></p>
        </div>
        <div class="paragraph">
          <p>주석의 전후에는 아래와 같이 공백을 삽입한다.</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p>명령문과 같은 줄에 주석을 붙일 때 <code>//</code> 앞</p>
            </li>
            <li>
              <p>주석 시작 기호 <code>//</code> 뒤</p>
            </li>
            <li>
              <p>주석 시작 기호 <code>/*</code> 뒤</p>
            </li>
            <li>
              <p>블록 주석을 한 줄로 작성시 종료 기호 <code>*/</code> 앞</p>
            </li>
          </ul>
        </div>
        <div class="listingblock">
          <div class="title">좋은 예</div>
          <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">/*
 * 공백 후 주석내용 시작
 */

System.out.print(true); // 주석 기호 앞 뒤로 공백

/* 주석내용 앞에 공백, 뒤에도 공백 */</code></pre>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="editorconfig">Appendix A: .editorconfig 파일 설정</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p><code>.editorconfig</code> 는 다양한 에디터와 IDE에서 공통적으로 지원하는 코드 스타일에 대한 설정 파일이다.
          자세한 스펙은 <a href="https://editorconfig.org/" class="bare">https://editorconfig.org/</a> 에서 파악할 수 있다.
          다양한 에디터로 파일을 고칠 때 같은 규칙을 참조할수 있도록 가급적 이 파일을 소스 저장소에서 올려서 공유하는 것을 권장한다.</p>
      </div>
      <div class="listingblock">
        <div class="title">`.editconfig`의 예제</div>
        <div class="content">
<pre class="highlight"><code class="language-properties" data-lang="properties"># top-most EditorConfig file
root = true

[*]
# [encoding-utf8]
charset = utf-8

# [newline-lf]
end_of_line = lf

# [newline-eof]
insert_final_newline = true

[*.bat]
end_of_line = crlf

[*.java]
# [indentation-tab]
indent_style = tab

# [4-spaces-tab]
indent_size = 4
tab_width = 4

# [no-trailing-spaces]
trim_trailing_whitespace = true

[line-length-120]
max_line_length = 120</code></pre>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="checkstyle">Appendix B: Checkstyle 사용법</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p>Checkstyle 은 코딩컨벤션 검사 도구이다. 이 가이드에서 안내하는 규칙을 검사하는 checkstyle  규칙 설정 파일을 제공한다.</p>
      </div>
      <div class="sect2">
        <h3 id="checkstyle-version">B.1. 필수 버전</h3>
        <div class="paragraph">
          <p>Checkstyle 8.24 버전 이상을 사용해야 한다. 빌드 도구와 IDE에서 권장한 버전을 쓰고 있는지 확인을 한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="checkstyle-rule-download">B.2. 규칙 설정 파일 다운로드</h3>
        <div class="paragraph">
          <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml" class="bare">https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml</a> 에서 다운로드한다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="checkstyle-rule-execution">B.3. 검사 실행</h3>
        <div class="paragraph">
          <p>실제 프로젝트에서 쓸 때는 IDE나 빌드도구와 연동해서 사용하는것을 권장한다. 그러나 규칙 파일을 커스터마이징 했을 때에는 Checkstyle을 독립적으로 실행을 해서 IDE나 빌드스크립트와 연동하기 전에 먼저 테스트해 보기를 권장한다.</p>
        </div>
        <div class="paragraph">
          <p>독립적으로 실행할 때는
            <a href="https://github.com/checkstyle/checkstyle/releases/" class="bare">https://github.com/checkstyle/checkstyle/releases/</a> 에서 jar 파일을 다운로드하고 아래와 같이 실행한다.</p>
        </div>
        <div class="listingblock">
          <div class="title">checkstyle 독립실행</div>
          <div class="content">
            <pre class="highlight"><code>java -jar checkstyle-8.24-all.jar -c [규칙파일] [소스폴더]</code></pre>
          </div>
        </div>
        <div class="paragraph">
          <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml">naver-checkstyle-rules.xml</a>을 수정 없이 사용할 때는  <code>-DsuppressionFile</code> 속성을 지정해야 한다.
            예외선언 파일의 위치를 IDE와 Maven/Gradle 빌드 양쪽에서 참조하기 위해서 필요한 속성이다.</p>
        </div>
        <div class="listingblock">
          <div class="title">naver-checkstyle-rules.xml 독립 실행 사례</div>
          <div class="content">
            <pre class="highlight"><code>java -DsuppressionFile=naver-checkstyle-suppressions.xml -jar checkstyle-8.24-all.jar -c naver-checkstyle-rules.xml src</code></pre>
          </div>
        </div>
        <div class="paragraph">
          <p>만약 검사 대상에서 제외할 파일이 없다면 <a href="#checkstyle-rule-suppressions-xml">제외 대상을 별도의 파일로 선언</a> 을 참조해서 <code>suppressionFile</code> 과 관련된 선언을 삭제하고 위의 명령에서도 생략할 수 있다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="checkstyle-rule-finding">B.4. 관련 규칙 확인 방법</h3>
        <div class="paragraph">
          <p>규칙 파일에서는 규칙의 ID를 주석으로 달았다. 경고 메시지에서도 규칙의 ID를 표시한다.</p>
        </div>
        <div class="listingblock">
          <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;!-- [1-line-package-import]--&gt;
&lt;module name="NoLineWrap"&gt;
    &lt;property name="tokens" value="PACKAGE_DEF, IMPORT"/&gt;
        &lt;message key="no.line.wrap"
            value="[1-line-package-import] {0} statement should not be line-wrapped."/&gt;
&lt;/module&gt;</code></pre>
          </div>
        </div>
        <div class="paragraph">
          <p>규칙의 ID를 이 가이드에서 검색해서 해당 규칙을 찾는다. HTML문서에서는 #뒤에 규칙의 ID를 붙여서 바로 이동할 수도 있다. 예를 들면 [need-brace]에 규칙에 대한 설명은 <a href="http://docs.navercorp.com/coding-convention/java.html#need-braces" class="bare">http://docs.navercorp.com/coding-convention/java.html#need-braces</a> 링크를 걸 수 있다. 온라인 코드 리뷰를 할 때도 이런 링크를 활용할 수 있다.</p>
        </div>
      </div>
      <div class="sect2">
        <h3 id="checkstyle-rule-limitation">B.5. 검사할 수 없는 규칙</h3>
        <div class="paragraph">
          <p>아래 규칙은 Checkstyle로 검사할 수 없다.</p>
        </div>
        <div class="ulist">
          <ul>
            <li>
              <p><a href="#avoid-korean-pronounce">한국어 발음대로의 표기 금지</a></p>
            </li>
            <li>
              <p><a href="#class-noun">클래스 이름에 명사 사용</a></p>
            </li>
            <li>
              <p><a href="#interface-noun-adj">인터페이스 이름에 명사/형용사 사용</a></p>
            </li>
            <li>
              <p><a href="#method-verb-preposition">메서드 이름은 동사/전치사로 시작</a></p>
            </li>
            <li>
              <p><a href="#test-class-suffix">테스트 클래스는 'Test’로 끝남</a></p>
            </li>
            <li>
              <p><a href="#space-after-bracket">대괄호 뒤에 공백 삽입</a></p>
            </li>
            <li>
              <p><a href="#space-around-comment">주석문 기호 전후의 공백 삽입</a></p>
            </li>
          </ul>
        </div>
      </div>
      <div class="sect2">
        <h3 id="checkstyle-rule-suppressions">B.6. 검사 대상에서 제외하기</h3>
        <div class="sect3">
          <h4 id="checkstyle-rule-suppressions-xml">B.6.1. 제외 대상을 별도의 파일로 선언</h4>
          <div class="paragraph">
            <p>Checkstyle에서는 검사대상에서 제외할 파일을 별도의 설정파일에서 지정할 수 있다.</p>
          </div>
          <div class="paragraph">
            <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml">naver-checkstyle-rules.xml</a>의 설정에서는 <code>suppressionFile</code> 이라는 속성으로 <code>naver-checkstyle-suppressions.xml</code> 파일의 위치를 지정할 수 있도록 미리 설정되어 있다.</p>
          </div>
          <div class="listingblock">
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">    &lt;module name="SuppressionFilter"&gt;
        &lt;property name="file" value="${suppressionFile}"/&gt;
        &lt;property name="optional" value="false"/&gt;
    &lt;/module&gt;</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p>굳이 예외로 지정할 파일이 없다면 <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml">naver-checkstyle-rules.xml</a>에서 위의 선언은 삭제하고 사용한다.</p>
          </div>
          <div class="paragraph">
            <p><code>suppressionFile</code> 속성으로 참조할 파일은 <code>naver-checkstyle-suppressions.xml</code> 과 같은 이름으로 지정한다.</p>
          </div>
          <div class="listingblock">
            <div class="title">naver-checkstyle-suppressions.xml 선언의 예</div>
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;?xml version="1.0"?&gt;
&lt;!DOCTYPE suppressions PUBLIC
"-//Puppy Crawl//DTD Suppressions 1.1//EN"
"http://www.puppycrawl.com/dtds/suppressions_1_1.dtd"&gt;

&lt;suppressions&gt;
    &lt;suppress files="UserController.java" checks=".*"/&gt;
    &lt;suppress files="UserService.java" checks=".*"/&gt;
&lt;/suppressions&gt;</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p>파일명을 정규식으로 설정하는 것도 가능하다. 자세한 선언 방법은 <a href="http://checkstyle.sourceforge.net/config_filters.html#SuppressionFilter" class="bare">http://checkstyle.sourceforge.net/config_filters.html#SuppressionFilter</a> 을 참조한다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="checkstyle-rule-suppressions-source">B.6.2. 제외할 영역을 주석으로 표시</h4>
          <div class="paragraph">
            <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml">naver-checkstyle-rules.xml</a> 의 설정에서는 아래와 같은 주석문을 인식한다.</p>
          </div>
          <div class="ulist">
            <ul>
              <li>
                <p><code>// @checkstyle:off</code> : 다음 행부터 검사 대상에서 제외</p>
              </li>
              <li>
                <p><code>// @checkstyle:on</code> : 다음 행부터 검사 대상에 포함</p>
              </li>
              <li>
                <p><code>// @checkstyle:ignore</code> // 같은 행의 소스를 검사하지 않음</p>
              </li>
            </ul>
          </div>
          <div class="listingblock">
            <div class="title">검사 대상에서 제외하는 주석 사용 예</div>
            <div class="content">
<pre class="highlight"><code class="language-java" data-lang="java">public class MyCAO { // @checkstyle:ignore 외부에 배포된 라이브러리
    public static final String SYSTEM_ID = "MD23D2";
    // @checkstyle:off
    public String CONNECT_URL;
    public String USER_ID;
    // @checkstyle:on
}</code></pre>
            </div>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="checkstyle-customizing">B.7. 커스터마이징</h3>
        <div class="paragraph">
          <p>`naver-checkstyle-rules.xml`에 정의된 규칙을 프로젝트에서 더 추가하거나, 수정해서 쓰려고 할 때 참고할만한 정보를 정리한다.</p>
        </div>
        <div class="sect3">
          <h4 id="checkstyle-customizing-abbr-list">B.7.1. 대문자로 표기할 약어를 추가</h4>
          <div class="paragraph">
            <p>'<a href="#list-uppercase-abbr">대문자로 표기할 약어 명시</a>' 규칙에 따라서 대문자로 표기할 약어는 따로 명시해야 한다. <code>naver-checkstyle-rules.xml</code> 파일에서 <code>allowedAbbreviations</code> 속성에 해당 단어를 추가한다.</p>
          </div>
          <div class="listingblock">
            <div class="title">대문자로 표기할 약어를 설정 파일에 명시</div>
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;!-- [list-uppercase-abbr] --&gt;
&lt;module name="AbbreviationAsWordInName"&gt;
    &lt;property name="ignoreFinal" value="false"/&gt;
    &lt;property name="allowedAbbreviationLength" value="1"/&gt;
    &lt;message key="abbreviation.as.word"
    value="[list-uppercase-abbr] Abbreviation in name ''{0}'' must contain no more than {1}"/&gt;
    &lt;property name="allowedAbbreviations" value="DAO,BO"/&gt;
&lt;/module&gt;</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p>설정 파일을 고치지 않으려면 `@checkstyle:ignore`와 같은 주석을 이용할 수도 있다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="checkstyle-customizing-indent">B.7.2. 들여쓰기에 탭 대신 스페이스 사용</h4>
          <div class="paragraph">
            <p>아래 선언을  <code>naver-checkstyle-rules.xml</code> 에서 삭제한다.</p>
          </div>
          <div class="listingblock">
            <div class="title">탭문자로 들여쓰도록 검사하는 규칙 선언</div>
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;!-- [indentation-tab] --&gt;
&lt;module name="RegexpSinglelineJava"&gt;
    &lt;property name="format" value="^\t* "/&gt;
    &lt;property name="message" value="[indentation-tab] Indent must use tab characters"/&gt;
    &lt;property name="ignoreComments" value="true"/&gt;
&lt;/module&gt;</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p>대신 아래와 같이 탭문자가 포함되어 있을때 경고를 보내는 선언을 추가한다.</p>
          </div>
          <div class="listingblock">
            <div class="title">스페이스로 들여쓰도록 검사하는 규칙 선언</div>
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;module name="FileTabCharacter"&gt;
    &lt;property name="eachLine" value="true"/&gt;
&lt;/module&gt;</code></pre>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="_빌드_도구_설정">Appendix C: 빌드 도구 설정</h2>
    <div class="sectionbody">
      <div class="sect2">
        <h3 id="_maven">C.1. Maven</h3>
        <div class="paragraph">
          <p>`pom.xml`에서 아래와 같은 선언을 추가한다.</p>
        </div>
        <div class="sect3">
          <h4 id="maven-encoding">C.1.1. 인코딩 지정</h4>
          <div class="paragraph">
            <p><code>pom.xml`의 `&lt;project/&gt;</code> 태그의 하위 요소로 아래와 같이 소스 파일의 인코딩을 <code>UTF-8</code> 로 명시한다.</p>
          </div>
          <div class="listingblock">
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;properties&gt;
    &lt;project.build.sourceEncoding&gt;UTF-8&lt;/project.build.sourceEncoding&gt;
&lt;/properties&gt;</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p>위의 속성값들은 <code>maven-compiler-plugin</code> 과 <code>maven-resources-plugin</code> 에서 기본값으로 참조된다.
              <code>&lt;plugins/&gt;</code> 선언부에서 직접 encoding을 명시하고 있다면 위의 속성이 참조되지 않는다.
              아래와 같은 경우이다.</p>
          </div>
          <div class="listingblock">
            <div class="title">Maven의 플러그인별 설정에서 인코딩 지정</div>
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;plugin&gt;
    &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
    &lt;artifactId&gt;maven-compiler-plugin&lt;/artifactId&gt;
    &lt;version&gt;3.1&lt;/version&gt;
    &lt;configuration&gt;
        &lt;source&gt;1.8&lt;/source&gt;
        &lt;target&gt;1.8&lt;/target&gt;
        &lt;encoding&gt;UTF-8&lt;/encoding&gt;
    &lt;/configuration&gt;
&lt;/plugin&gt;
&lt;plugin&gt;
    &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
    &lt;artifactId&gt;maven-resources-plugin&lt;/artifactId&gt;
    &lt;version&gt;2.7&lt;/version&gt;
    &lt;configuration&gt;
        &lt;encoding&gt;UTF-8&lt;/encoding&gt;
    &lt;/configuration&gt;
&lt;/plugin&gt;</code></pre>
            </div>
          </div>
        </div>
        <div class="sect3">
          <h4 id="maven-editorconfig">C.1.2. editorconfig 플러그인 설정</h4>
          <div class="paragraph">
            <p><a href="https://github.com/ec4j/editorconfig-maven-plugin" class="bare">https://github.com/ec4j/editorconfig-maven-plugin</a> 을 참고한다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="maven-checkstyle">C.1.3. Checkstyle 플러그인 설정</h4>
          <div class="paragraph">
            <p><code>&lt;build&gt;</code> 태그 아래에 <code>&lt;pluginManagement/&gt;</code> 선언에 maven-checkstyle-plugin의 버전과 checkstyle의 버전을 명시한다.
              checkstyle의 버전은 반드시 8.24 이상으로 지정한다.</p>
          </div>
          <div class="paragraph">
            <p>예외를 선언할 파일이 없다면 <code>naver-checkstyle-suppressions.xml</code> 과 관련된 설정은 생략해도 된다.</p>
          </div>
          <div class="listingblock">
            <div class="title">pluginManagement 선언</div>
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;pluginManagement&gt;
    &lt;plugins&gt;
        &lt;plugin&gt;
            &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
            &lt;artifactId&gt;maven-checkstyle-plugin&lt;/artifactId&gt;
            &lt;version&gt;3.1.1&lt;/version&gt;
            &lt;configuration&gt;
                &lt;configLocation&gt;naver-checkstyle-rules.xml&lt;/configLocation&gt;
                &lt;sourceDirectories&gt;${project.build.sourceDirectories}&lt;/sourceDirectories&gt;
                &lt;propertyExpansion&gt;suppressionFile=./naver-checkstyle-suppressions.xml&lt;/propertyExpansion&gt;
            &lt;/configuration&gt;
            &lt;dependencies&gt;
                &lt;dependency&gt;
                    &lt;groupId&gt;com.puppycrawl.tools&lt;/groupId&gt;
                    &lt;artifactId&gt;checkstyle&lt;/artifactId&gt;
                    &lt;version&gt;8.24&lt;/version&gt;
                &lt;/dependency&gt;
            &lt;/dependencies&gt;
        &lt;/plugin&gt;
    &lt;/plugins&gt;
&lt;/pluginManagement&gt;</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p><code>&lt;build&gt;</code> → <code>&lt;plugins&gt;</code> 태그 아래에 다음과 같은 선언을 추가한다.</p>
          </div>
          <div class="listingblock">
            <div class="title">plugin 선언</div>
            <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;plugin&gt;
    &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
    &lt;artifactId&gt;maven-checkstyle-plugin&lt;/artifactId&gt;
&lt;/plugin&gt;</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p><code>mvn checkstyle:checkstyle`로 실행하면 검사가 시작된다. `mvn site</code> 명령으로 검사를 실행하고 싶다면 <code>&lt;reporting&gt;</code> → `&lt;plugins&gt;`태그 아래에 위의 선언을 추가한다.</p>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="_gradle">C.2. Gradle</h3>
        <div class="paragraph">
          <p>Gradle 버전 5.4.1 이상을 권장한다.</p>
        </div>
        <div class="sect3">
          <h4 id="gradle-encoding">C.2.1. 인코딩 지정</h4>
          <div class="paragraph">
            <p>Java plugin의 속성으로 인코딩을 지정한다. 아래와 같이 여러 방법이 가능하다.</p>
          </div>
          <div class="listingblock">
            <div class="title">java plugin의 속성에서 인코딩을 지정</div>
            <div class="content">
<pre class="highlight"><code class="language-groovy" data-lang="groovy">plugins {
    id 'java'
}

...

// 방법1
compileJava.options.encoding = 'UTF-8'
compileTestJava.options.encoding = 'UTF-8'

// 방법 2
[compileJava, compileTestJava]*.options*.encoding = 'UTF-8'

// 방법 3
tasks.withType(Compile) {
    options.encoding = 'UTF-8'
}</code></pre>
            </div>
          </div>
        </div>
        <div class="sect3">
          <h4 id="gradle-editorconfig">C.2.2. .editorconfig 플러그인 설정</h4>
          <div class="paragraph">
            <p><a href="https://github.com/ec4j/editorconfig-gradle-plugin">editorconfig-gradle-plugin</a>을 설정하면 <code>.editorconfig</code> 의 선언과 어긋나는 파일이 존재하면 빌드를 실패하게 만들수 있다.
              아래와 같이 `build.gradle`에 선언한다.</p>
          </div>
          <div class="listingblock">
            <div class="content">
<pre class="highlight"><code class="language-groovy" data-lang="groovy">plugins {
    id 'org.ec4j.editorconfig' version '0.0.3'

}
editorconfig {
    excludes = ['build']
}

check.dependsOn editorconfigCheck</code></pre>
            </div>
          </div>
        </div>
        <div class="sect3">
          <h4 id="gradle-checkstyle">C.2.3. Checkstyle 플러그인 설정</h4>
          <div class="paragraph">
            <p>아래와 같이 `build.gradle`에 선언한다.</p>
          </div>
          <div class="listingblock">
            <div class="content">
<pre class="highlight"><code class="language-groovy" data-lang="groovy">plugins {
    id 'checkstyle'
}

checkstyle {
    maxWarnings = 0 // 규칙이 어긋나는 코드가 하나라도 있을 경우 빌드 fail을 내고 싶다면 이 선언을 추가한다.
    configFile = file("${rootDir}/naver-chestyle-rules.xml")
    configProperties = ["suppressionFile" : "${rootDir}/naver-checkstyle-suppressions.xml"]
    toolVersion ="8.24"  // checkstyle 버전 8.24 이상 선언
}</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p>예외를 선언할 파일이 없다면 <code>naver-style-supressions.xml</code> 관련 선언은 생략할 수 있다.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="sect1">
    <h2 id="editor-config">Appendix D: 편집기 설정</h2>
    <div class="sectionbody">
      <div class="paragraph">
        <p>이 가이드의 규칙을 지키는데 도움이 되는 코드 편집기와 뷰어 설정 방법을 정리한다.</p>
      </div>
      <div class="sect2">
        <h3 id="_eclipse">D.1. Eclipse</h3>
        <div class="sect3">
          <h4 id="eclipse-imports">D.1.1. <code>Organize Imports</code> 설정</h4>
          <div class="paragraph">
            <p>아래 규칙을 자동으로 지키도록 해준다.</p>
          </div>
          <div class="ulist">
            <ul>
              <li>
                <p><a href="#avoid-star-import">static import에만 와일드 카드 허용</a></p>
              </li>
              <li>
                <p><a href="#import-grouping"><code>import</code> 선언의 순서와 빈 줄 삽입</a></p>
              </li>
            </ul>
          </div>
          <div class="paragraph">
            <p>아래와 같은 순서로 설정한다.</p>
          </div>
          <div class="olist arabic">
            <ol class="arabic">
              <li>
                <p>importorder 설정 파일 다운로드</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p><code>naver.importorder</code> 파일을 <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver.importorder" class="bare">https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver.importorder</a> 에서 다운로드한다.</p>
                    </li>
                  </ul>
                </div>
              </li>
              <li>
                <p><code>Organize Imports</code> 설정 화면으로 이동</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p>Workspace 전역설정은 `Window &gt; Preference &gt; Java &gt; Code style &gt; Organize Imports`로 이동.</p>
                    </li>
                    <li>
                      <p>프로젝트별 설정은 `Porject &gt; Properties &gt; Java Code style &gt; Organize Imports`로 이동.</p>
                    </li>
                  </ul>
                </div>
              </li>
              <li>
                <p>`Organize Imports`의 항목 입력</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p><code>Enable project specific settings</code>(프로젝트별 설정의 경우) : 체크</p>
                    </li>
                    <li>
                      <p><code>Define the sorting order of import statement</code></p>
                      <div class="ulist">
                        <ul>
                          <li>
                            <p><code>[Import]</code> 버튼을 클릭하여 `naver.importorder`파일 선택</p>
                          </li>
                        </ul>
                      </div>
                    </li>
                    <li>
                      <p><code>Number of imports needed for .*</code> : 99</p>
                    </li>
                    <li>
                      <p><code>Number of static imports needed for .*</code> : 1</p>
                    </li>
                  </ul>
                </div>
              </li>
            </ol>
          </div>
          <div class="paragraph">
            <p><span class="image"><img src="images/eclipse-imports.png" alt="Eclipse Organize Imports" width="50%"></span></p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="eclipse-formatter">D.1.2. Formatter 설정</h4>
          <div class="paragraph">
            <p>들여쓰기, 공백, 줄바꿈 규칙을 지키도록 도와준다.</p>
          </div>
          <div class="olist arabic">
            <ol class="arabic">
              <li>
                <p>Formatter 설정 파일 다운로드</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p><code>naver-eclipse-formatter.xml</code> 파일을 <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-eclipse-formatter.xml" class="bare">https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-eclipse-formatter.xml</a> 에서 다운로드한다.</p>
                    </li>
                  </ul>
                </div>
              </li>
              <li>
                <p><code>Formatter</code> 메뉴로 이동</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p>Workspace 전역설정은 `Window &gt; Preference &gt; Java &gt; Code style &gt; Formatter`에서 이동한다.</p>
                    </li>
                    <li>
                      <p>프로젝트별 설정은 `Project &gt; Properties &gt; Java Code style &gt; Formatter`로 이동한다.</p>
                    </li>
                  </ul>
                </div>
              </li>
              <li>
                <p><code>Formatter</code> 항목 설정</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p>프로젝트별 설정의 경우 `Enable project specific settings`를 선택한다.</p>
                    </li>
                    <li>
                      <p><code>[Import]</code> 버튼을 누른 후, 다운로드 한 <code>naver-eclipse-formatter.xml</code> 파일을 선택한다.</p>
                    </li>
                    <li>
                      <p>`[OK]`버튼을 누른다.</p>
                    </li>
                  </ul>
                </div>
              </li>
            </ol>
          </div>
          <div class="paragraph">
            <p>Formatter가 설정되면 코드 편집창에서 <code>Ctrl + Shift + f</code> 키로 코드 포멧을 맞출 수 있다. Formatter가 자동으로 맞춰주는 결과가  들지 않을 수도 있기 때문에 선택적으로 사용한다. 예를 들면 줄바꿈 후 들여쓰기를 최소기준인 한 단계보다 깊게 하고 싶을 경우 포멧터를 쓰지 않고 직접 탭문자를 입력할 수도 있다.  Eclipse의 포멧터는 Checkstyle에서 검사하는 규칙보다 더 구체적인 규칙으로 코드를 맞춰 주기도 한다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="eclipse-save-actions">D.1.3. <code>Save actions</code> 활용</h4>
          <div class="paragraph">
            <p>Eclipse에서는 `Ctrl + s`키로 파일을 저장할때 수행하는 동작을 지정할 수 있다. 아래와 같이 메뉴로 이동한다.</p>
          </div>
          <div class="ulist">
            <ul>
              <li>
                <p>Workspace 전역 설정 : <code>Window &gt; Preference &gt; Java &gt; Editor Save Actions</code></p>
              </li>
              <li>
                <p>프로젝트별 설정 : <code>Project &gt; Properties &gt; Java Editor &gt; Save Actions</code></p>
              </li>
            </ul>
          </div>
          <div class="paragraph">
            <p>해당 메뉴에서 설정할 수 있는 동작은 아래와 같다.</p>
          </div>
          <div class="ulist">
            <ul>
              <li>
                <p><code>Format source code</code> : Formatter에 정의된 포메팅을 적용한다. 프로젝트의 상황에 따라서 선택한다.</p>
              </li>
              <li>
                <p><code>Organize imports</code> : `Ctrl + Shift + o`를 눌렀을 때와 동일한 동작을 한다.</p>
              </li>
              <li>
                <p><code>Additional Actions</code> : 아래 2개의 동작은 설정을 권장한다.</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p><code>Convert control statement bodies to block</code> : `{}`가 없는 제어문에 `{}`을 넣어준다.'<a href="#need-braces">조건/반복문에 중괄호 필수 사용</a>' 규칙을 준수하게 해준다.</p>
                    </li>
                    <li>
                      <p><code>Remove trailing white spaces on all line</code> : 줄끝에 붙은 공백을 제거한다. '<a href="#no-trailing-spaces">공백으로 줄을 끝내지 않음</a>' 규칙을 준수하게 해준다.</p>
                    </li>
                  </ul>
                </div>
              </li>
            </ul>
          </div>
        </div>
        <div class="sect3">
          <h4 id="eclipse-cleanup">D.1.4. 포멧터 일괄 적용  활용</h4>
          <div class="paragraph">
            <p><code>Cleanup</code> 기능으로 프로젝트의 전체 소스에 포멧터를 일괄적으로 적용할 수 있다.
              예를 들면 '<a href="#no-trailing-spaces">공백으로 줄을 끝내지 않음</a>' 규칙을 준수하기 위해 프로젝트의 모든 파일에서 줄 마지막의 공백을 일괄적으로 없애는 작업을 하는 경우에 사용할 수 있다.</p>
          </div>
          <div class="paragraph">
            <p><code>Source &gt; Clean up..</code> 메뉴로 실행한다. 여러 프로젝트에 반복적으로 수행해야할 작업의 그룹이 있다면, 수행할 작업을 별도의 프로파일로 빼서 정의할 수도 있다. 사전정의된 프로파일을 실행할때는 <code>Use configured profiles`를 선택한다. `Use custom profile</code> 을 선택하면 수행할 작업을 하나씩 선택할 수 있다.</p>
          </div>
          <div class="paragraph">
            <p><span class="image"><img src="images/eclipse-cleanup.png" alt="Eclipose의 Cleanup 기능" width="50%"></span></p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="eclipse-checkstyle">D.1.5. Checkstyle 설정</h4>
          <div class="sect4">
            <h5 id="_플러그인_설치">플러그인 설치</h5>
            <div class="olist arabic">
              <ol class="arabic">
                <li>
                  <p>메뉴에서 `Help &gt; Eclise Marketplace`에서 'Checkstyle plugin’으로 검색한다.</p>
                </li>
                <li>
                  <p>Eclipse Checkstyle plugin(eclipse-cs)를 찾아서 <code>[Install]</code> 버튼을 누른다.</p>
                </li>
              </ol>
            </div>
            <div class="paragraph">
              <p>이미 플러그인을 설치했다면 권장하는 버전이 설치되어 있는지 확인을 한다. <code>Help &gt; Installation Details</code> 메뉴에서 이를 확인할 수 있다.
                Eclipse Checkstyle plugin의 버전은  의존하는 checkstyle의 버전과 동일하게 표기되고 있다. `naver-checkstyle-rules.xml`을 수정없이 쓸 때는 Eclipse Checkstyle plugin의 버전도 8.24 이상인지 확인을 한다.</p>
            </div>
            <div class="paragraph">
              <p><span class="image"><img src="images/eclipse-checkstyle-install.png" alt="Eclipse Checkstyle plugin 설치" width="50%"></span></p>
            </div>
          </div>
          <div class="sect4">
            <h5 id="_규칙_파일_불러오기">규칙 파일 불러오기</h5>
            <div class="olist arabic">
              <ol class="arabic">
                <li>
                  <p><code>Checkstyle</code> 메뉴로 이동</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p>여러 프로젝트에서 같은 파일을 활용할 때는 Workspace 전역 규칙으로 불러 올것을 권장한다. <code>Window &gt; Preference &gt; Checkstyle</code> 메뉴로 이동한다.</p>
                      </li>
                      <li>
                        <p>프로젝트별로 다른 설정을 쓸 때는 프로젝트별 설정을 해야한다. <code>Project &gt; Properties &gt; Checkstyle</code> 메뉴에서 <code>Local Check Configurations</code> 탭으로 이동한다.</p>
                      </li>
                    </ul>
                  </div>
                </li>
                <li>
                  <p><code>Checkstyle</code> 메뉴에서 설정파일 목록의 오른쪽에 있는 <code>[New]</code> 버튼을 누른다.</p>
                </li>
                <li>
                  <p><code>Checkstyle Configuration Properties</code> 팝업창의 항목 입력</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><code>Type</code> : <code>External Configuration File</code> 혹은 <code>Project Relative Configuration</code> 선택</p>
                      </li>
                      <li>
                        <p><code>Location</code> : `[Browse]`버튼을 눌러서 `naver-checkstyle-rules.xml`를 찾아서 선택</p>
                      </li>
                      <li>
                        <p><code>Name</code> : 인식할 수 있는 이름. `naver-checkstyle-rules`를 권장</p>
                      </li>
                      <li>
                        <p><code>Protect Checkstyle Configuration File</code> : 체크</p>
                      </li>
                    </ul>
                  </div>
                </li>
              </ol>
            </div>
          </div>
          <div class="sect4">
            <h5 id="_프로젝트별_검사_설정">프로젝트별 검사 설정</h5>
            <div class="paragraph">
              <p><code>Project &gt; Properties &gt; Checkstyle</code> 메뉴에서  아래 항목을 설정한다.</p>
            </div>
            <div class="ulist">
              <ul>
                <li>
                  <p><code>Checkstyle active for this project</code> : 체크</p>
                </li>
                <li>
                  <p><code>Write formatter/cleanup config (experimental!)</code> : 체크하지 않음</p>
                </li>
                <li>
                  <p><code>Simple - use the following check configuration for all files</code> : 앞 단계에서 설정한 <code>naver-checkstyle-rules</code> 선택</p>
                </li>
                <li>
                  <p><code>Excluding from checking</code></p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><code>files outside sourcxe directories</code> : 체크</p>
                      </li>
                      <li>
                        <p><code>derived (generated) files</code> : 체크</p>
                      </li>
                    </ul>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div class="sect3">
          <h4 id="eclipse-show-whitespaces">D.1.6. 공백 문자 보이기 설정</h4>
          <div class="paragraph">
            <p>탭과 스페이스가 섞여 있는 프로젝트의 코드를 정리할 때는 탭과 스페이스를 눈에 보이게 표시한다.
              <code>Windows &gt; Preferences &gt; Editors &gt; Text Editors</code> 에서 <code>Show whitespaces characters</code> 를 선택한다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="eclipse-customizing">D.1.7. 커스터마이징</h4>
          <div class="paragraph">
            <p>이 가이드와 함께 제공되는 Eclipse의 설정파일이 프로젝트에서 재정의한 규칙과 맞지 않을 때 참고할만한 정보를 정리한다.</p>
          </div>
          <div class="sect4">
            <h5 id="_들여쓰기에_탭_대신_스페이스_사용">들여쓰기에 탭 대신 스페이스 사용</h5>
            <div class="paragraph">
              <p>Eclipse는 들여쓰기로 4개 크기의 탭을 디폴트로 사용한다. <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-eclipse-formatter.xml">naver-eclipse-formatter.xml</a>에서도 동일하게 설정되어 있다.</p>
            </div>
            <div class="paragraph">
              <p>만약 탭 대신 스페이스로 들여쓰기를 하려는 프로젝트에서는 아래와 같이 설정한다.</p>
            </div>
            <div class="ulist">
              <ul>
                <li>
                  <p>`Windows &gt; Preferences &gt; Editors &gt; Text Editors`에 메뉴로 이동한다.</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p>`Insert spaces for Tab`를 선택한다.</p>
                      </li>
                    </ul>
                  </div>
                </li>
              </ul>
            </div>
            <div class="paragraph">
              <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-eclipse-formatter.xml">naver-eclipse-formatter.xml</a>에 반영하려면 <code>tabulation.char</code> 속성을 <code>space</code> 로 바꾼다.</p>
            </div>
            <div class="listingblock">
              <div class="title">Eclipse formatter 탭문자 설정</div>
              <div class="content">
                <pre class="highlight"><code class="language-xml" data-lang="xml">&lt;setting id="org.eclipse.jdt.core.formatter.tabulation.char" value="space"/&gt;</code></pre>
              </div>
            </div>
          </div>
          <div class="sect4">
            <h5 id="_줄바꿈_후_추가_들여쓰기_단계_조정">줄바꿈 후 추가 들여쓰기 단계 조정</h5>
            <div class="paragraph">
              <p>Eclipse의 자동 포멧 기능을 적용했을 때 (단축키 <code>Ctrl+Shift+f</code> ) 적용되는 기준이다.
                이 저장소에서 제공하는 <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-eclipse-formatter.xml">naver-eclipse-formatter.xml</a> 파일의 설정으로는 문장에서 <code>;</code> 을 선언하기 전 중간에 줄바꿈을 했을 때 1단계의 들어쓰기가 추가된다.</p>
            </div>
            <div class="paragraph">
              <p>이를 2단계로 바꾸려면 <code>Java Code Style &gt; Formatter &gt; [Edit] &gt; Line Wrapping &gt; General settings</code> 의 아래 항목을 조정한다.</p>
            </div>
            <div class="ulist">
              <ul>
                <li>
                  <p><code>Default indention for warpped lines:</code> : 2</p>
                </li>
                <li>
                  <p><code>Default indention for array initalizers:</code> : 2</p>
                </li>
              </ul>
            </div>
            <div class="paragraph">
              <p><span class="image"><img src="images/eclipse-line-wrapping.png" alt="IntelliJ 줄바꿈 들여쓰기 설정" width="50%"></span></p>
            </div>
            <div class="paragraph">
              <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-eclipse-formatter.xml">naver-eclipse-formatter.xml</a> 에서는 <code>continuation_indentation</code> 관련 속성을 2로 바꾸면 위와 같은 효과가 있다.</p>
            </div>
            <div class="listingblock">
              <div class="title">Eclipse formatter에서 들어쓰기 단계 조정</div>
              <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">&lt;setting id="org.eclipse.jdt.core.formatter.continuation_indentation_for_array_initializer" value="2"/&gt;
&lt;setting id="org.eclipse.jdt.core.formatter.continuation_indentation" value="2"/&gt;</code></pre>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="_intellij">D.2. IntelliJ</h3>
        <div class="sect3">
          <h4 id="intellij-formatter">D.2.1. Formatter 적용</h4>
          <div class="paragraph">
            <p><code>naver-intellij-formatter.xml</code> 파일을 아래와 같이 적용한다.</p>
          </div>
          <div class="olist arabic">
            <ol class="arabic">
              <li>
                <p>포멧터 다운로드</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-intellij-formatter.xml" class="bare">https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-intellij-formatter.xml</a> 에서 <code>naver-intellij-formatter.xml</code> 을 다운로드 한다.</p>
                    </li>
                  </ul>
                </div>
              </li>
              <li>
                <p>Scheme 설정</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p><code>File &gt; Settings</code> 메뉴로 이동한다. (단축키 <code>Alt + Shift + S</code> )</p>
                    </li>
                    <li>
                      <p><code>Editor &gt; Code Style &gt; Java</code> 항목으로 이동한다.</p>
                    </li>
                    <li>
                      <p><code>Scheme</code> 항목의 오른쪽에 있는 톱니바퀴 아이콘을 클릭한다.</p>
                    </li>
                    <li>
                      <p><code>Import Scheme &gt; IntelliJ IDEA Code Style XML</code> 을 선택한다.</p>
                    </li>
                    <li>
                      <p><span class="image"><img src="images/intellij-formatter-import.png" alt="IntelliJ Formatter Import" width="50%"></span></p>
                    </li>
                    <li>
                      <p>1에서 다운로드한 <code>naver-intellij-formatter.xml</code> 파일을 선택한후 <code>[OK]</code> 버튼을 누른다.</p>
                    </li>
                    <li>
                      <p><span class="image"><img src="images/intellij-formatter-import-scheme.png" alt="IntelliJ Formatter Import Scheme" width="50%"></span></p>
                    </li>
                    <li>
                      <p><code>TO</code> 항목에는 <code>naver-intellij-formatter.xml</code> 안에 선언된 'Naver-Coding-Convnetion-v1.2’와 같은 이름이 디폴트로 나온다. 이 이름은 IntelliJ에서 전역적인 식별자가 되어서 다른 프로젝트에도 참조가 된다. 포멧터를 커스터 마이징했거나 프로젝트마다 다른 포멧터 설정을 쓴다면 이 스키마의 이름이 유일성 있게 인지되도록 수정한다.</p>
                    </li>
                    <li>
                      <p>Settings 레이어의 <code>[OK]</code> 버튼을 누른다.</p>
                    </li>
                  </ul>
                </div>
              </li>
            </ol>
          </div>
        </div>
        <div class="sect3">
          <h4 id="_항목별_수동_설정">D.2.2. 항목별 수동 설정</h4>
          <div class="paragraph">
            <p>만약 이 가이드에서 제공하는 <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-intellij-formatter.xml">naver-intellij-formatter.xm</a> 설정을 활용하기가 어려운 상황이라면 최소한 아래의 항목들은 직접 설정한다.</p>
          </div>
          <div class="sect4">
            <h5 id="_들여쓰기">들여쓰기</h5>
            <div class="paragraph">
              <p>'<a href="#indentation-tab">하드탭 사용</a>' , '<a href="#4-spaces-tab">탭의 크기는 4개의 스페이스</a>' 설정을 준수하기 위한 설정이다.</p>
            </div>
            <div class="ulist">
              <ul>
                <li>
                  <p><code>File &gt; Settings &gt; Editor &gt; Code Style &gt; Java</code> 메뉴로 이동</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><code>User tab charactor</code> : 선택</p>
                      </li>
                      <li>
                        <p><code>Tab Size</code>, <code>Indent</code> : 4</p>
                      </li>
                    </ul>
                  </div>
                </li>
              </ul>
            </div>
          </div>
          <div class="sect4">
            <h5 id="_import_구문">Import 구문</h5>
            <div class="paragraph">
              <p>'<a href="#avoid-star-import">static import에만 와일드 카드 허용</a>', '<a href="#import-grouping"><code>import</code> 선언의 순서와 빈 줄 삽입</a>' 설정을 준수하기 위한 설정이다.</p>
            </div>
            <div class="paragraph">
              <p><code>File &gt; Settings &gt; Editors &gt; Code Style &gt; Java &gt; Imports &gt; Import Layout</code> 로 이동해서 아래 항목을 설정한다.</p>
            </div>
            <div class="ulist">
              <ul>
                <li>
                  <p>General</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><code>Use single class import</code> : 체크</p>
                      </li>
                      <li>
                        <p><code>Class count to use import with '*'</code> : 99</p>
                      </li>
                      <li>
                        <p><code>Names count to use static import with '*'</code> : 1</p>
                      </li>
                    </ul>
                  </div>
                </li>
                <li>
                  <p>Import Layout</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><a href="#import-grouping"><code>import</code> 선언의 순서와 빈 줄 삽입</a>의 순서대로 지정</p>
                      </li>
                      <li>
                        <p>모든 세부 그룹 사이에도 공백을 넣어야 Eclipse의 Formatter와 동일하게 정렬함.</p>
                      </li>
                    </ul>
                  </div>
                </li>
              </ul>
            </div>
            <div class="paragraph">
              <p><span class="image"><img src="images/intellij-imports.png" alt="IntelliJ Imports 설정" width="50%"></span></p>
            </div>
          </div>
          <div class="sect4">
            <h5 id="_줄바꿈_시_연산자_위치">줄바꿈 시 연산자 위치</h5>
            <div class="paragraph">
              <p>'<a href="#line-wrapping-position">줄바꿈 허용 위치</a>' 규칙에 따라 연산자 전에 줄바꿈을 해야한다. 자동 정렬 시에 이를 준수하기 위해서 아래와 같이 설정한다.</p>
            </div>
            <div class="olist arabic">
              <ol class="arabic">
                <li>
                  <p><code>File &gt; Settings &gt; Editors &gt; Code Style &gt; Java &gt; Imports &gt; Import Layout</code> 로 이동한다.</p>
                </li>
                <li>
                  <p><code>Binary expressions</code> 아래의 <code>Operation sign on next line</code> 항목을 선택한다.</p>
                </li>
              </ol>
            </div>
            <div class="paragraph">
              <p><span class="image"><img src="images/intellij-oper-sign.png" alt="IntelliJ Wrapping and Braces 설정" width="50%"></span></p>
            </div>
          </div>
        </div>
        <div class="sect3">
          <h4 id="intellij-saveactions">D.2.3. 파일의 마지막에 새줄 문자가 없는 경우 추가</h4>
          <div class="paragraph">
            <p><a href="#newline-eof">파일의 마지막에는 새줄</a> 규칙을 준수하기 위한 설정이다.
              <code>File</code> &gt; <code>Settings</code> &gt; <code>Editor</code> &gt; <code>General</code> 메뉴에서 <code>Ensure line feed at file end on Save</code>  를 선택한다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="intellij-save-actions">D.2.4. 파일을 저장 할 때마다 포멧터 자동 적용</h4>
          <div class="paragraph">
            <p><a href="https://plugins.jetbrains.com/plugin/7642-save-actions">Save Actions plugin</a>을 활용하면 파일을 저장하는 순간 포멧터를 자동 적용할 수 있다.</p>
          </div>
          <div class="olist arabic">
            <ol class="arabic">
              <li>
                <p><code>File</code> &gt; <code>Settings</code> ( <code>Ctrl + Alt + S</code> ) &gt; <code>Plugins</code> 메뉴로 이동</p>
              </li>
              <li>
                <p><code>Marketplace</code> 탭에서 'Save Actions' 로 검색</p>
              </li>
              <li>
                <p><code>Save Actions' plugin의 상세 설명 화면에서  `[Install]</code> 버튼 클릭</p>
              </li>
              <li>
                <p>IntelliJ를 재시작</p>
              </li>
              <li>
                <p><code>File</code> &gt; <code>Settings</code> &gt; <code>Other Settions</code> &gt; <code>Save Actions</code> 메뉴로 이동</p>
              </li>
              <li>
                <p>아래 항목을 체크</p>
                <div class="ulist">
                  <ul>
                    <li>
                      <p><code>Activate save actions on save</code></p>
                    </li>
                    <li>
                      <p><code>Optimize imoprts</code></p>
                    </li>
                    <li>
                      <p><code>Refomat file</code></p>
                    </li>
                  </ul>
                </div>
              </li>
            </ol>
          </div>
        </div>
        <div class="sect3">
          <h4 id="intellij-project-processing">D.2.5. 일괄 변환</h4>
          <div class="paragraph">
            <p>프로젝트의 홈디렉토리에 커서를 놓은채로 아래의 메뉴를 실행하면 프로젝트의 모든 소스에 해당 설정을 일괄 적용한다.</p>
          </div>
          <div class="ulist">
            <ul>
              <li>
                <p><code>File &gt; Line Separators</code></p>
              </li>
              <li>
                <p><code>Code &gt; Reformat Code</code></p>
              </li>
              <li>
                <p><code>Code &gt; Auto-Indent Lines</code></p>
              </li>
              <li>
                <p><code>Code &gt; Optimize Imports</code></p>
              </li>
            </ul>
          </div>
        </div>
        <div class="sect3">
          <h4 id="intellij-checkstyle">D.2.6. Checkstyle 설정</h4>
          <div class="sect4">
            <h5 id="_플러그인_설치_2">플러그인 설치</h5>
            <div class="olist arabic">
              <ol class="arabic">
                <li>
                  <p><code>File &gt; Settings &gt; Plugins</code> 메뉴로 이동한다.</p>
                </li>
                <li>
                  <p><code>[Browse Reposities..]</code> 버튼 클릭</p>
                </li>
                <li>
                  <p>'Checkstyle’의 단어로 검색해서 CheckStyle-IDEA 플러그인을 찾은 후 <code>[Install]</code> 버튼을 클릭</p>
                </li>
              </ol>
            </div>
            <div class="paragraph">
              <p>이미 플러그인이 설치되어 있다면 권장하는 버전인지 확인을 한다.
                CheckStyle-IDEA의 사용여부를 선택하는 화면에서 'This plugin provides both real-time and on-demand scanning of Java files with CheckStyle 8.24 from within IDEA.'와 같은 문구로 Checkstyle의 버전을 알려준다.
                <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml">naver-checkstyle-rules.xml</a> 을 수정없이 쓰려면 Checkstyle 8.24이상을 쓰는 CheckStyle-IDEA의 버전이 설치되어 있어야한다.</p>
            </div>
            <div class="paragraph">
              <p><span class="image"><img src="images/intellij-checkstyle-install.png" alt="CheckStyle-IDEA" width="50%"></span></p>
            </div>
          </div>
          <div class="sect4">
            <h5 id="_검사_설정">검사 설정</h5>
            <div class="olist arabic">
              <ol class="arabic">
                <li>
                  <p><code>File &gt; Settings &gt; Other Settings &gt; Checkstyle</code> 메뉴에서 아래 항목들을 설정 한다</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><code>Checkstyle versions</code> : 8.24 이상 선택. 디폴트 설정과 다르다면 'Apply' 버튼을 한번 눌러준다.</p>
                      </li>
                      <li>
                        <p><code>Scan scope</code> : <code>All sources including tests</code> 선택</p>
                      </li>
                      <li>
                        <p><code>Treat Checkstyle errors as warnings</code> : 체크</p>
                      </li>
                    </ul>
                  </div>
                </li>
                <li>
                  <p><code>File &gt; Settings &gt; Other Settins &gt; Checkstyle</code> 메뉴로 이동한다.</p>
                </li>
                <li>
                  <p><code>[+]</code> 버튼을 누르면 나오는 입력창에서 아래 항목을 입력한다.</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><code>Description</code> : 식별할 수 있는 이름. <code>Naver Checkstyle Rules [버전]</code> 를 권장한다. 프로젝트별로 커스터마이징을 했다면 식별하기 쉽게 프로젝트 이름 등을 붙인다.</p>
                      </li>
                      <li>
                        <p><code>Use a Local Checkstyle File</code> : 선택하고 <code>[Browse]</code> 버튼을 눌러서 `naver-checkstyle-rules.xml`을 지정한다.</p>
                      </li>
                      <li>
                        <p><code>[Next]</code> 버튼을 누른다.</p>
                      </li>
                    </ul>
                  </div>
                </li>
                <li>
                  <p><code>suppressionFile</code> 변수를 설정하라는 화면이 나오면</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><span class="image"><img src="images/intellij-checkstyle-suppressions.png" alt="IntelliJ Checkstyle config_loc" width="50%"></span></p>
                      </li>
                      <li>
                        <p>검사 예외를 지정하지 않는다면 <code>[Next]</code> 버튼을 누른다.</p>
                      </li>
                      <li>
                        <p>예외 정책을 지정할 <code>naver-checkstyle-suppressions.xml</code> 이 있을 경우에는 파일의 위치를 입력한 후 <code>[Next]</code> 버튼을 누른다. 프로젝트 루트에서 상대경로로 입력해도 된다.</p>
                      </li>
                    </ul>
                  </div>
                </li>
                <li>
                  <p><code>naver-checkstyle-rules</code> 규칙을 앞의 체크박스를 선택한다.</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><span class="image"><img src="images/intellij-checkstyle-settings.png" alt="IntelliJ Checkstyle 설정" width="50%"></span></p>
                      </li>
                    </ul>
                  </div>
                </li>
              </ol>
            </div>
            <div class="admonitionblock warning">
              <table>
                <tbody><tr>
                  <td class="icon">
                    <div class="title">Warning</div>
                  </td>
                  <td class="content">
                    Checkstyle의 상위 버전에서 하위 호환성으로 인한 문제가 생길 경우 <code>Checkstyle versions</code> 항목을 <code>8.24</code> 로 고정하면 <a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-checkstyle-rules.xml">naver-checkstyle-rules.xml</a> 을 사용할 수 있다.
                  </td>
                </tr>
                </tbody></table>
            </div>
          </div>
        </div>
        <div class="sect3">
          <h4 id="intellij-show-whitespace">D.2.7. 공백 문자 보이기 설정</h4>
          <div class="paragraph">
            <p>탭과 스페이스가 섞여 있는 프로젝트의 코드를 정리할 때는 탭과 스페이스를 눈에 보이게 표시한다.
              <code>File &gt; Settings &gt; Editor &gt; General &gt; Appearance`에서 `Show whitespaces`를 선택한다.
                하위 분류에서 `Leading</code>, <code>Inner</code>,<code>Trailing</code> 을 선택한다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="intellij-customizing">D.2.8. 커스터마이징</h4>
          <div class="paragraph">
            <p>이 가이드와 함께 제공되는 IntelliJ의 설정파일이 프로젝트에서 재정의한 규칙과 맞지 않을 때 참고할만한 정보를 정리한다.</p>
          </div>
          <div class="sect4">
            <h5 id="_들여쓰기에_탭_대신_스페이스_사용_2">들여쓰기에 탭 대신 스페이스 사용</h5>
            <div class="paragraph">
              <p>이 가이드의 규칙과 다르게 탭대신 스페이스로 들여쓰기를 하고 싶다면 아래와 같이 설정한다.</p>
            </div>
            <div class="olist arabic">
              <ol class="arabic">
                <li>
                  <p><code>File &gt; Settings &gt; Editor &gt; Code Style &gt; Java</code> 메뉴로 이동한다.</p>
                </li>
                <li>
                  <p><code>Tabs and Indents</code> 탭으로 이동해서 아래 항목을 입력한다.</p>
                  <div class="ulist">
                    <ul>
                      <li>
                        <p><code>Use tab charactor</code> : 미선택</p>
                      </li>
                      <li>
                        <p><code>Tab size</code> : 4</p>
                      </li>
                    </ul>
                  </div>
                </li>
              </ol>
            </div>
          </div>
          <div class="sect4">
            <h5 id="_줄바꿈_후_추가_들여쓰기_단계_조정_2">줄바꿈 후 추가 들여쓰기 단계 조정</h5>
            <div class="paragraph">
              <p>IntelliJ의 자동 포멧 기능을 적용했을 때 (단축키 <code>Ctrl+Shift+f</code> ) 적용되는 기준이다.
                이 저장소에서 제공하는 <code>naver-intellij-formatter.xml</code> 파일의 설정으로는 문장에서 <code>;</code> 을 선언하기 전 중간에 줄바꿈을 했을 때 1단계의 들어쓰기가 추가된다.</p>
            </div>
            <div class="paragraph">
              <p>이를 2단계로 바꾸려면 아래와 같이 설정한다.</p>
            </div>
            <div class="olist arabic">
              <ol class="arabic">
                <li>
                  <p><code>File &gt; Settings &gt; Editor &gt; Code Style &gt; Java</code> 메뉴로 이동한다.</p>
                </li>
                <li>
                  <p><code>Tabs and Indents</code> 탭으로 이동한다.</p>
                </li>
                <li>
                  <p><code>Continuation ident:</code> 항목을 8로 입력한다.</p>
                </li>
              </ol>
            </div>
            <div class="paragraph">
              <p><span class="image"><img src="images/intellij-indents.png" alt="IntelliJ Indents 설정" width="50%"></span></p>
            </div>
            <div class="paragraph">
              <p><a href="https://github.com/naver/hackday-conventions-java/blob/master/rule-config/naver-intellij-formatter.xml">naver-intellij-formatter.xml</a> 파일에서는 <code>CONTINUATION_INDENT_SIZE</code> 속성을 8로 선언해서 반영할 수 있다.</p>
            </div>
            <div class="listingblock">
              <div class="title">IntelliJ formatter에서 들어쓰기 단계 조정</div>
              <div class="content">
<pre class="highlight"><code class="language-xml" data-lang="xml">    &lt;indentOptions&gt;
        &lt;option name="CONTINUATION_INDENT_SIZE" value="8" /&gt;
        &lt;option name="USE_TAB_CHARACTER" value="true" /&gt;
    &lt;/indentOptions&gt;</code></pre>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="_vi">D.3. VI</h3>
        <div class="sect3">
          <h4 id="vi-tabsize">D.3.1. 탭의 크기 지정</h4>
          <div class="paragraph">
            <p>Unix/Linux는 1탭이 8자리인데 이는 이 가이드의 <a href="#4-spaces-tab">탭의 크기는 4개의 스페이스</a> 규칙에 맞지 않는다.
              별다른 설정없이 Java 소스를 vi에서 확인하는 경우에는 혼란을 유발할 수 있다.
              <code>[home]/.vimrc</code> 파일에서 다음을 설정한다.</p>
          </div>
          <div class="listingblock">
            <div class="content">
<pre class="highlight"><code>set tabstop=4
set shiftwidth=4</code></pre>
            </div>
          </div>
          <div class="paragraph">
            <p>tabstop은 <code>\t`문자를 몇개의 크기로 보여줄지를, shiftwidth는 `&gt;&gt;</code>, <code>&lt;&lt;</code> 키를 이용할 때 들어가는 간격을 지정한다.</p>
          </div>
        </div>
        <div class="sect3">
          <h4 id="vi-textwidth">D.3.2. 한 줄 최대길이</h4>
          <div class="paragraph">
            <p>'<a href="#line-length-120">최대 줄 너비는 120</a>' 규칙을 준수하기 위해 ‘textwidth’ 옵션을 사용한다.</p>
          </div>
          <div class="listingblock">
            <div class="content">
              <pre class="highlight"><code>set textwidth=120</code></pre>
            </div>
          </div>
        </div>
      </div>
      <div class="sect2">
        <h3 id="_github">D.4. Github</h3>
        <div class="paragraph">
          <p>Github.com과 Github Enterprise를 사용할 때도 탭의 크기 등을 맞춰야 IDE를 쓸 때와 일관된 레이아웃으로 코드 리뷰를 할 수 있다.
            <code>.editorconfig</code> 파일을 프로젝트 최상위 디렉토리에 올리면 해당 저장소의 코드 보기/ 편집 기능에서 일괄적으로 탭의 크기 등이 설정된다.
            <a href="#editorconfig">.editorconfig 파일 설정</a> 를 참고한다.</p>
        </div>
        <div class="paragraph">
          <p>만약 저장소 전체 설정을 하기 어려울 경우, 코드를 보는 URL 뒤에 `?ts=4`파라미터를 붙이면 탭의 크기를 지정할 수 있다.
            예를 들면 <a href="https://github.com/naver/ngrinder/blob/master/ngrinder-controller/src/test/java/org/ngrinder/AbstractNGrinderTransactionalTest.java?ts=4" class="bare">https://github.com/naver/ngrinder/blob/master/ngrinder-controller/src/test/java/org/ngrinder/AbstractNGrinderTransactionalTest.java?ts=4</a> 와 같은 식이다.</p>
        </div>
      </div>
    </div>
  </div>
</div>
<div id="footer">
  <div id="footer-text">
    Version unspecified<br>
    Last updated 2020-07-24 22:56:25 +0900
  </div>
</div>

</body>

https://naver.github.io/hackday-conventions-java/

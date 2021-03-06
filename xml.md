# XML (Extensible Markup Language)

XML(Extensible Markup Language)은 W3C에서 개발된, 다른 특수한 목적을 갖는 마크업 언어를 만드는데 사용하도록 권장하는 다목적 마크업 언어이다. XML은 주로 다른 종류의 시스템, 특히 인터넷에 연결된 시스템끼리 데이터를 쉽게 주고 받을 수 있게 하여 HTML의 한계를 극복할 목적으로 만들어졌다.

XML은 텍스트 데이터 형식으로 유니코드를 사용해 전 세계 언어를 지원한다. XML을 설계할 때는 주로 문서를 표현하는데 집중했지만, 지금은 임의의 자료구조(portable data)를 나타내는 데 널리 쓰인다. 대표적인 예가 웹 서비스이다.

많은 API가 개발되어 XML 데이터를 처리하고자 하는 소프트웨어 개발자들이 여러 가지 스키마 시스템이 있어서 XML 기반 언어의 정의를 보다 쉽게 할 수 있도록 도와준다. (Reference : https://en.wikipedia.org/wiki/XML)

구분 | SGML | HTML | XML  
:----: | :----: | :----: | :----: 
복잡도<br>(Complexity) | Complicated | Simple | Normal
확장성<br>(Scalability) | Possible | Impossible | Possible
태그정의<br>(Tag definition) | Possible | Impossible | Possible
스펙<br>(Spec) | Complicated | Simple | Simple
검색방식<br>(Search) | Structural | All | Structural
스타일<br>(Style) | DSSSL | CSS | XSL
S/W | litte & expensive | many & cheap | many & cheap

XML 문서는 다음과 같이 분류된다.

* Well-formed document 
    
    * 구문이 일반적인 규칙을 따른다는 의미를 말하며, HTML과 달리 구문의 체크가 까다롭다.

        * Case sensitive 
        * Closing Tags
        * No Overlapping Tags
        * Root Element
        * Attribute : name = 'value' or name = "value"

* Valid Document

    * XML 문서가 DTD(Document Type Definition)나 Schema에 맞게 되어 있는지를 검사하게 된다. 일반적으로 Parser는 XML 문서에 대해서 먼저 정적형식(well-formed)을 따르고 있는지 검사하고, 그 다음 DTD의 구조에 대한 규정을 따르고 있는지를 검사하게 된다.

    * 즉, valid문서는 well-formed 문서이면서 DTD나 Schema에 정의된 형식에 맞는 문서를 지칭한다.

## 구성 (Composition)

### 타입 선언 (Type declaration)

xml 문서의 타입 선언은 다음과 같이 버전과 인코딩 방식과 standalone 속성을 선언 및 정의한다.

```xml
<?xml version="1.0" encoding="utf-8" standalone="yes">
```
해당 문서 외에 다른 문서가 필요할 경우 standalone 속성은 "no"가 되어야 한다.

### Element 

XML 문서의 가장 기초를 구성하는 정보와 구조적 정의를 포함한다.
태그 이름은 숫자로 시작하지 않는다.
태그명 사이에 공백은 허용하지 않는다.
빈태그에서 /다음에 공백을 허용하지 않는다.

```xml
ex)  <age> 25 </age>;
```

### 속성 (Attribute)

```xml
ex)  <tagname   attribute="value">
        :
    </tagname>;
```

### CDATA 세션

```xml
<comparsion>
    <less> <![CDATA[2<3]]> </less>
    <greater> <![CDATA[4>2]]> </greater>
</comparsion>
```

### Namespace

XMl은 tag 이름을 사용자가 임의로 정할 수 있기 때문에 여러 문서에서 요소(태그) 이름이 동일해질 수 있다. 문서들을 동시에 처리하고자 할 때 이름이 중복될 수 있다. 이 때 name은 URI에 의해 구별하고, Namespace는 여러 개의 document에 포함된 element와 attribute를 구별하는 데 사용한다.

```xml
<root   xmlns:car="http://www.carpro.co.kr"
        xmlns:book="http://www.bookstore.com">
        <car:part>
            <hood color="blue"/>
            <windshiled tint="no"/>
        </car:part>
        <book:part id="part 1">
            <title> Romeo episode </title>
            <summary> ... </summary>
        </book:part>
</root>
```

## XML API

### **SAX (Simple API for XML)**

SAX는 XML 문서를 파싱하는 도중 발생하는 이벤트('<>'를 만나거나 '</>'를 만나는 경우)에 의해 작동한다.

* Serial access mechanism

* Event-driven

* Fastest and least memory-intensive mechanism

* Searchable only

DOM이 random access가 가능한 반면 SAX는 serial access만 가능하다.

#### SAX Event handler

SAX parser는 XMLReader 인터페이스를 구현하며, parse() 메소드에 의해 작동을 시작한다. 이후 xml 문서를 파싱하는 도중 발생하는 정상 또는 에러 상황에 이벤트를 발생시키고 핸들러에게 처리를 위임한다.

SAX 이벤트 핸들러의 기본 인터페이스는 다음과 같다.

* DTD Handler : DTD 내용 중 NOTATION 선언, 언파스트 ENTITY 선언
* ContentHandler : XML 문서내의 element, text, PI
* Entity Resolver : DTD나 XML 문서 내용 중 외부 파스트 ENTITY 참조
* ErrorHandler : error 처리

Default Handler를 상속받아 필요한 경우 이벤트 처리 메소드를 재정의할 수 있다.

```java
/**
  * 문서 시작 시 호출된다.
  */
@Override
public void startDocument() throws SAXException {
    System.out.println("Document starts.");
}
/**
  * 문서 종료 시 호출된다.
  */
@Override
public void endDocument() throws SAXException {
    System.out.println("Document ends.");
}
/**
  * Element 시작 시 호출된다.
  */
@Override
public void startElement(String uri, String localName, String qName, Attributes attributes) throws SAXException {
    switch (qName) {
    case "booklist":
        System.out.println("<booklist>");
        break;
    case "isbn":
        System.out.print("		<isbn>");
        break;
    case "book": // 속성이 존재하는 tag
        System.out.println("	<book " + attributes.getQName(0) + "='" + attributes.getValue(0)+"'>");
        break;
    case "title":
        System.out.print("		<title>");
        break;
    case "publisher":
        System.out.print("		<publisher>");
        break;
    case "price":
        System.out.print("		<price>");
        break;
    default:
        System.out.print("		<others>");
        break;
    }
}
/**
  * Element 종료 시 호출된다.
  */
@Override
public void endElement(String uri, String localName, String qName) throws SAXException {
    switch (qName) {
    case "booklist":
        System.out.println("</booklist>");
        break;
    case "isbn":
        System.out.println("</isbn>");
        break;
    case "book":
        System.out.println("	</book>");
        break;
    case "title":
        System.out.println("</title>");
        break;
    case "publisher":
        System.out.println("</publisher>");
        break;
    case "price":
        System.out.println("</price>");
        break;
    default:
        System.out.println("</others>");
        break;
    }
}
/**
  * Text 만날 시 호출된다.
  */
@Override
public void characters(char[] ch, int start, int length) throws SAXException {
    System.out.print(new String(ch, start, length).trim());
}
```


### **DOM (Document Object Model)**

DOM은 특정 브라우저나 구현언어에 의존적이지 않는 프로그래밍을 위한 IDL(Interface Definition Language) 기술로 API가 설계되었다. DOM을 사용하게 되면 언어에 구분없이 동일한 스펙으로 메소드를 사용하게 되는 결과를 갖게 된다. 기본적으로 DOM은 XML 문서를 객체로 조작하고 접근하는 데에 필요한 최소한의 인터페이스만을 정의한다. 또한, 문서의 생성, 탐색, 내용 추가, 삭제, 수정 기능을 제공한다.

* Random access mechanism

* Tree mechanism

* Less programming than SAX

* Can modify, replace, add, delete


Node | Node name | Node value 
:----: | :----: | :----: 
Element | 태그이름 | null
Attr | 속성이름 | 속성값
Text | #text | 노드의 내용
CDATASection| #cdata-section | 노드의 내용
EntityReference|참조된 엔티티의 이름|null
Entity|선언된 엔티티의 이름| null
ProcessingInstruction|PI의 이름|PC이름을 제외한 전체 내용
Comment | #comment | 주석 내용
Document| #document | null
DocumentType| DTD 이름 | null
DocumentFragment| #document-fragment|null
Notation |선언 이름|null

#### 요소 추출

```java
/**
  * 지정된 노드 아래 노드들 추출하는 방법
  * @param n 지정된 노드
  */
public static void getNode(Node n) {
    for(Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
        System.out.println(ch.getNodeName());
    }
}
/**
  * 지정된 노드 아래 노드들 추출하는 방법
  * @param n 지정된 노드
  */
public static void getNode2(Node n) {
    NodeList list = n.getChildNodes();
    for(int i = 0; i < list.getLength(); ++i) {
        System.out.println(list.item(i).getNodeName());
    }
}
/**
  * 지정된 노드 아래 element명만 추출
  * @param n 지정된 노드
  */
public static void getNode3(Node n) {
    for(Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
        if(ch.getNodeType() == Node.ELEMENT_NODE)
            System.out.println(ch.getNodeName());
    }
}
/**
 * 전체 노드 검색
 * @param n 지정된 노드
 */
public static void getNode4(Node n) {
	for (Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
		if (ch.getNodeType() == Node.ELEMENT_NODE) {
			System.out.println(ch.getNodeName());
			getNode4(n); // recursive current node
		}
	}
}
/**
 * 공백을 제외한 텍스트만 추출
 * @param n 지정된 노드
 */
public static void getNode5(Node n) {
	for (Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
		if (ch.getNodeType() == Node.ELEMENT_NODE) {
			System.out.println(ch.getNodeName());
			getNode5(n); // recursive current node
		}
		else if(ch.getNodeType() == Node.TEXT_NODE && ch.getNodeValue().trim().length() != 0) {
			System.out.println(ch.getNodeValue());
		}
	}
}
```

이외에도 DOM 방식은 여러가지 추가, 삭제 기능 등을 지원한다.

```java
/**
 * 지정된 노드에 element를 추가하는 메소드
 * @param n 지정된 노드
 */
public static void addNode(Node n) {
    for (Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
    if (ch.getNodeType() == Node.ELEMENT_NODE) {
            if(ch.getNodeName().equals("node name")) {
                Document doc = ch.getOwnerDocument(); 
                Element comp = doc.createElement("create node name"); // create node element
                Text txt = doc.createTextNode("create text value"); // create text node
                ch.appendChild(comp); 
                comp.appendChild(txt);
            }
            addNode(n); // recursive current node
        }
    }
}
/**
 * 지정된 노드에 element를 삭제하는 메소드
 * @param n 지정된 노드
 */
public static void deleteNode(Node n) {
    for (Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
        if (ch.getNodeType() == Node.ELEMENT_NODE) {
            if(ch.getNodeName().equals("node name")) {
                Node parent = ch.getParentNode(); // get parent
                parent.removeChild(ch); // remove current
            }
            deleteNode(n); // recursive current node
        }
    }
}
/**
 * 지정된 노드에 속성을 추가하는 메소드
 * @param n 지정된 노드
 */
public static void addNodeAttribute(Node n) {
    for (Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
        if (ch.getNodeType() == Node.ELEMENT_NODE) {
            if(ch.getNodeName().equals("node name")) {
                Element element = (Element)ch;
                element.setAttribute("attribute name", "value");
            }
            addNodeAttribute(n); // recursive current node
        }
    }
}
/**
 * 지정된 노드에 속성을 삭제하는 메소드
 * @param n 지정된 노드
 */
public static void deleteNodeAttribute(Node n) {
    for (Node ch = n.getFirstChild(); ch != null; ch = ch.getNextSibling()) {
        if (ch.getNodeType() == Node.ELEMENT_NODE) {
            if(ch.getNodeName().equals("node name")) {
                NamedNodeMap attributeMap = ch.getAttributes();
                attributeMap.removeNamedItem("attribute name");
            }
            deleteNodeAttribute(n); // recursive current node
        }
    }
}
```

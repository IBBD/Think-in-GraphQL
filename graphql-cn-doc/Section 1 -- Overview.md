# Overview

GraphQL是一个查询语言，通过提供直观且灵活的语法和系统来构建客户端程序，而且还能描述它们的数据需求及其相互作用。

例如，这个GraphQL请求将会从GraphQL的服务器端接收id=4的用户名。


```graphql
{
  user(id: 4) {
    name
  }
}
```

其返回的结果数据如下:

```js
{
  "user": {
    "name": "Mark Zuckerberg"
  }
}
```

GraphQL不是一门普通意义上的编程语言，没有按照标准的编程语言或者存储系统那样实现，而是为应用服务提供了一个统一的语言，类型系统和哲学。它能为产品开发提供统一的接口，也能为工具构建提供一个强大的平台。

GraphQL is not a programming language capable of arbitrary computation, but is
instead a language used to query application servers that have
capabilities defined in this specification. GraphQL does not mandate a
particular programming language or storage system for application servers that
implement it. Instead, application servers take their capabilities and map them
to a uniform language, type system, and philosophy that GraphQL encodes.
This provides a unified interface friendly to product development and a powerful
platform for tool-building.

下面是GraphQL的主要设计目标：

GraphQL has a number of design principles:

 * **Hierarchical**: Most product development today involves the creation and
   manipulation of view hierarchies. To achieve congruence with the structure
   of these applications, a GraphQL query itself is structured hierarchically.
   The query is shaped just like the data it returns. It is a natural
   way for clients to describe data requirements.
 
 * **分层的**：今天，大都是产品在开发的时候就涉及视图层次结构的创建及操纵。为了实现应用之间结构的一致性，GraphQL查询自身就是分层结构的。GraphQL查询和数据的返回类似，对客户端来说，它是一种描述数据需求的很自然的方式。

 * **Product-centric**: GraphQL is unapologetically driven by the requirements
   of views and the front-end engineers that write them. GraphQL starts with
   their way of thinking and requirements and build the language and runtime
   necessary to enable that.

 * **以产品为中心**：GraphQL是以需求为驱动的，并主要提供给前端工程师去使用。GraphQL是从大家思考问题的方式和需求出发，构建的语言。

 * **Strong-typing**: Every GraphQL server defines an application-specific
   type system. Queries are executed within the context of that type system.
   Given a query, tools can ensure that the query is both syntactically
   correct and valid within the GraphQL type system before execution, i.e. at
   development time, and the server can make certain guarantees about the shape
   and nature of the response.

 * **强类型**：每一个GraphQL服务器都定义了应用指定的类型系统，而查询就执行在这些类型系统的语境（context）中。对于一个查询，工具能在执行之前确定该查询语句的语法是否正确，例如在开发的时候；另外，服务器也能保证返回值的格式与类型。

 * **Client-specified queries**: Through its type system, a GraphQL server
   publishes the capabilities that its clients are allowed to consume. It is
   the client that is responsible for specifying exactly how it will consume
   those published capabilities. These queries are specified at field-level
   granularity. In the majority of client-server applications written
   without GraphQL, the server determines the data returned in its various
   scripted endpoints. A GraphQL query, on the other hand, returns exactly what
   a client asks for and no more.

 * **客户端指定查询**：通过类型系统，GraphQL服务器能发布相应的功能特性，而怎么使用这些特性，则是由客户端来决定。客户端可以在字段粒度上，对查询进行控制。在大多数没有使用GraphQL的C/S应用中，数据的返回是由服务器来决定的。而对应一个GraphQL查询，返回是由客户端请求的。

 * **Introspective**: GraphQL is introspective. A GraphQL server's type system
   must be queryable by the GraphQL language itself, as will be described in this
   specification. GraphQL introspection serves as a powerful platform for
   building common tools and client software libraries.

 * **内省的**：GraphQL服务器的类型系统必须是能被GraphQL语言所查询的，也能为其所描述。对于创建公共的工具库和客户端的代码库，GraphQL的内省服务是一个强大的平台。

Because of these principles, GraphQL is a powerful and productive environment
for building client applications. Product developers and designers building
applications against working GraphQL servers -- supported with quality tools --
can quickly become productive without reading extensive documentation and with
little or no formal training. To enable that experience, there must be those
that build those servers and tools.

The following formal specification serves as a reference for those builders.
It describes the language and its grammar, the type system and the
introspection system used to query it, and the execution and validation engines
with the algorithms to power them. The goal of this specification is to provide
a foundation and framework for an ecosystem of GraphQL tools, client libraries,
and server implementations -- spanning both organizations and platforms -- that
has yet to be built. We look forward to working with the community
in order to do that.

---
title: 11.6.1 Components
date: 2018-12-14 14:53:13
tags:
---

> 注：高亮处为感觉翻译不明白的地方

# 11.6.1 概要 Summary
This sub clause specifies a set of constructs that can be used to define software systems of arbitrary size and complexity. In particular, it specifies a Component as a modular unit with well-defined Interfaces that is replaceable within its environment. The Component concept addresses the area of component-based development and component-based system structuring, where a Component is modeled throughout the development life cycle and successively refined into deployment and run-time.

本小节规定了一组可用于定义任意大小和复杂度的软件系统的构造。尤其是，它将组件指定为模块化单元，具有明确定义的接口，可在其环境中替换。组件概念涉及基于组件的开发和基于组件的系统结构领域，其中组件在整个开发生命周期中建模，并且相继进入部署和运行时。

An important aspect of component-based development is the reuse of previously constructed Components. A Component can always be considered an autonomous unit within a system or subsystem. It has one or more provided and/or required Interfaces (potentially exposed via Ports), and its internals are hidden and inaccessible other than as provided by its Interfaces. Although it may be dependent on other elements in terms of Interfaces that are required, a Component is encapsulated and its Dependencies are designed such that it can be treated as independently as possible. As a result, Components and subsystems can be flexibly reused and replaced by connecting (“wiring”) them together.
 The aspects of autonomy and reuse also extend to Components at deployment time. The artifacts that implement Component are intended to be capable of being deployed and re-deployed independently, for instance to update an existing system.

它具有一个或多个提供的和（或）必需的接口（可能通过Ports暴露），并且其内部是隐藏的，其提供接口之外的部分是不可访问。 ==虽然它可能依赖于所需的接口方面的其他元素，但是组件被封装并且其依赖关系被设计为使得可以尽可能独立地对待它。
==<span data-type="color" style="color:rgb(46, 48, 51)"><span data-type="background" style="background-color:rgb(255, 255, 255)">因此，组件和子系统可以灵活地重用，并通过将它们连接在一起(&quot;wiring&quot;)来替换它们。</span></span>autonomy 和 reuse 方面也被扩展到组件的部署。artifacts 实现组件的意义在于可独立部署和重新部署，例如，更新现有的系统。

The Components package supports the specification of both logical Components (e.g., business components, process components) and physical Components (e.g., EJB components, CORBA components, COM+ and .NET components, WSDL components, etc.), along with the artifacts that implement them and the nodes on which they are deployed and executed. It is anticipated that profiles based around Components will be developed for specific component technologies and associated hardware and software environments.

Components package 规范支持逻辑组件（例如：业务组件、流程组件）和物理组件（如：EJB组件、CORBA组件、COM+、.NET 组件, WSDL 组件等），以及实现他们的 artifacts 与部署和执行它们的节点。==预计将针对特定组件技术以及相关的硬件和软件环境开发基于组件的配置文件。==

# 11.6.2 抽象语法 Abstract Syntax


略

# 11.6.3 语义 Semantics

## 11.6.3.1 组件 Components
A Component represents a modular part of a system that encapsulates its contents and whose manifestation is replaceable within its environment.

<span data-type="color" style="color:rgb(46, 48, 51)"><span data-type="background" style="background-color:rgb(255, 255, 255)">组件表示系统的模块部分，该模块封装其内容，其表现形式在其环境中是可替换的。</span></span>

A Component is a *self-contained* unit that encapsulates the state and behavior of a number of Classifiers. A Component specifies a formal contract of the services that it provides to its clients and those that it requires from other Components or services in the system in terms of its provided and required Interfaces.

组件是个独立的单元，它封装了许多 Classifiers 状态和行为。<span data-type="color" style="color:rgb(46, 48, 51)"><span data-type="background" style="background-color:rgb(255, 255, 255)">组件根据其提供和需要的接口，指定它向客户端提供的服务以及它从系统中的其他组件或服务中需要服务的正式契约。</span></span>

A Component is a *substitutable *unit that can be replaced at design time or run-time by a Component that offers equivalent functionality based on compatibility of its Interfaces. As long as the environment is fully compatible with the provided and required Interfaces of a Component, it will be able to interact with this environment. Similarly, a system can be extended by adding new Component types that add new functionality. Larger pieces of a system’s functionality may be assembled by reusing Components as parts in an encompassing Component or assembly of Components, and wiring them together.

<span data-type="color" style="color:rgb(51, 51, 51)">组件是一个可替换的单元，可以在设计时或运行时由基于接口兼容性提供等效功能的组件替换。只要环境与组件提供的和需要的接口完全兼容，它就能够与该环境交互。类似地，可以通过添加添加新功能的新组件类型来扩展系统。系统功能的较大部分可以通过重用组件作为包含组件或组件组装中的部件进行组装，并将它们连接在一起。</span>

<span data-type="color" style="color:rgb(51, 51, 51)">A Component is modeled throughout the development life cycle and successively refined into deployment and run-time. A Component may be manifested by one or more Artifacts, and in turn, that Artifact may be deployed to its execution environment. A DeploymentSpecification may define values that parameterize the Component’s execution. (See Deployments – Clause 19).</span>

组件在整个开发生命周期中建模，然后依次细化为部署和运行时。组件可以由一个或多个工件表示，然后，该工件可以部署到其执行环境中。部署规范可以定义参数化组件执行的值。(参见部署-第19条)。

The required and provided Interfaces of a Component allow for the specification of StructuralFeatures such as attributes and Association ends, as well as BehavioralFeatures such as Operations and Receptions. A Component may implement a provided Interface directly, or its realizing Classifiers may do so, or they may be inherited. The required and provided Interfaces may optionally be organized through Ports; these enable the definition of named sets of provided and required Interfaces that are typically (but not always) addressed at run-time.

组件所需和提供的接口允许对结构特性(如属性和关联端点)以及行为特性(如操作和接收)进行规范。组件可以直接实现提供的接口，或者它的实现分类器可以这样做，或者它们可以被继承。所需和提供的接口可以选择通过端口组织;它们支持定义提供的和需要的接口的命名集，这些接口通常(但不总是)在运行时处理。

A Component has an external view (or “black-box” view) by means of its publicly visible Properties and Operations. Optionally, a Behavior such as a ProtocolStateMachine may be attached to an Interface, Port, and to the Component itself, to define the external view more precisely by making dynamic constraints in the sequence of Operation calls explicit.

组件通过其公开可见的属性和操作具有外部视图（或“黑盒”视图）。 可选地，可以将诸如ProtocolStateMachine的行为附加到接口，端口和组件本身，以通过使操作调用序列中的动态约束显式来更精确地定义外部视图。

The wiring between Components in a system or other context can be structurally defined by using Dependencies between compatible simple Ports, or between Usages and matching InterfaceRealizations that are represented by sockets and lollipops (see 10.4.4) on Components on Component diagrams. Creating a wiring Dependency between a Usage and a matching InterfaceRealization, or between compatible simple Ports, means that there may be some additional information, such as performance requirements, transport bindings, or other policies that determine that the Interface is realized in a way that is suitable for consumption by the depending Component. Such additional information could be captured in a profile by means of stereotypes.

系统或其他上下文中的组件之间的连接可以通过使用兼容的简单端口之间的依赖关系，或者在组件图上的组件上使用套接字和棒棒糖(请参见10.4.4)表示的使用和匹配的接口实现来进行结构定义。创建一个连接依赖使用和匹配InterfaceRealization之间,或兼容之间简单的端口,意味着可能会有一些额外的信息,比如性能要求,传输绑定或其他政策,确定接口实现的方式适用于消费的不同组件。这些额外的信息可以通过原型在概要文件中捕获。

A Component also has an internal view (or “white-box” view) by means of its private Properties and realizing Classifiers. This view shows how the external Behavior is realized internally. Dependencies on the external view provide a convenient overview of what may happen in the internal view; they do not prescribe what must happen. More detailed behavior specifications such as Interactions and Activities may be used to detail the mapping from external to internal behavior.

通过私有属性和实现分类器，组件还具有内部视图(或“白盒”视图)。这个视图显示了外部行为是如何在内部实现的。对外部视图的依赖关系可以方便地概述内部视图中可能发生的情况;他们没有规定必须发生什么。更详细的行为规范，例如交互和活动，可以用来详细描述从外部到内部行为的映射。

The execution time semantics for an assembly Connector in a Component are that requests (signals and operation invocations) travel along an instance of a Connector. The execution semantics for multiple Connectors directed to and from different roles, or n-ary Connectors where n> 2, indicates that the instance that will originate or handle the request will be determined at execution time.

组件中组装连接器的执行时间语义是请求(信号和操作调用)沿着连接器的实例传递。指向不同角色和来自不同角色的多个连接器的执行语义，或n-ary连接器(其中n> 2)的执行语义指示将在执行时确定发起或处理请求的实例。

<span data-type="color" style="color:rgb(51, 51, 51)">A number of UML standard stereotypes exist that apply to Component. For example, «Subsystem» to model large-scale Components, and «Specification» and «Realization» to model Components with distinct specification and realization definitions, where one specification may have multiple realizations (see the Standard Profiles).</span>

存在许多应用于组件的UML标准构造型。例如，将«子系统»建模为大型组件，将«规范»和«实现»建模为具有不同规范和实现定义的组件，其中一个规范可能有多个实现(请参阅标准配置文件)。

<span data-type="color" style="color:rgb(51, 51, 51)">A Component may be realized (or implemented) by a number of Classifiers. In that case, a Component owns a set of ComponentRealizations to these Classifiers.</span>

组件可以由许多分类器实现(或实现)。在这种情况下，组件拥有这些分类器的一组组件实现。

A component acts like a Package for all model elements that are involved in or related to its definition, which should be either owned or imported explicitly. Typically the Classifiers that realize a Component are owned by it.

组件的作用类似于其定义中涉及或与之相关的所有模型元素的包，这些模型元素应该显式地拥有或导入。通常，实现组件的分类器属于组件。

The isDirectlyInstantiated property specifies the kind of instantiation that applies to a Component. If false, the Component is instantiated as an addressable object. If true, the Component is defined at design-time, but at run-time (or executiontime) an object specified by the Component does not exist, that is, the Component is instantiated indirectly, through the instantiation of its realizing Classifiers or parts.

isDirectlyInstantiated属性指定应用于组件的实例化类型。如果为false，则将组件实例化为可寻址对象。如果为真，组件是在设计时定义的，但是在运行时(或执行时)，组件指定的对象不存在，也就是说，组件是通过实例化其实现的分类器或部件间接实例化的。

# 11.6.4 符合 Notation



A Component is shown as a Classifier rectangle with the keyword «component». Optionally, in the right hand corner a Component icon can be displayed. This is a Classifier rectangle with two smaller rectangles protruding from its left hand side. If the icon symbol is shown, the keyword «component» may be hidden.

组件显示为带有关键字«component»的分类器矩形。还可以选择在右下角显示组件图标。这是一个分类器矩形，两个较小的矩形从它的左手边突出。如果显示图标符号，则可能隐藏关键字«component»。

The attributes, operations and internal structure compartments all have their normal meaning. The internal structure uses the notation defined in StructuredClassifiers (11.2).

属性、操作和内部结构划分都有其正常的含义。内部结构使用StructuredClassifiers(11.2)中定义的表示法。

The provided and required Interfaces of a Component may be shown by means of ball (lollipop) and socket notation (see 10.4.4), where the lollipops and sockets stick out of the Component rectangle.

组件提供和需要的接口可以通过球(棒棒糖)和套接字符号(见10.4.4)来显示，其中棒棒糖和套接字伸出组件矩形。

For displaying the full signature of a provided or required Interface of a Component, the Interfaces can also be displayed as normal expandable Classifier rectangles. For this option, the Interface rectangles are connected to the Component rectangle by appropriate dependency arrows, as specified in 7.7.4 and 10.4.4.

为了显示组件提供的或需要的接口的完整签名，这些接口也可以显示为普通的可扩展分类器矩形。对于这个选项，接口矩形通过适当的依赖箭头连接到组件矩形，如7.7.4和10.4.4中指定的那样。

A conforming tool may optionally support compartments named “provided interfaces” and “required interfaces” listing the provided and required Interfaces by name. This may be a useful option in scenarios in which a Component has a large number of provided or required Interfaces.

符合规范的工具可以选择性地支持命名为“提供的接口”和“必需的接口”的区域，按名称列出提供的和必需的接口。在组件具有大量提供的或需要的接口的场景中，这可能是一个有用的选项

Additional optional compartments “realizations” and “artifacts” may be used to list the realizing Classifiers (Classifiers reached by following the realization property) and manifesting Artifacts (Artifacts that manifest this component – see 19.3).

其他可选的部分“实现”和“工件”可以用来列出实现的分类器(通过遵循实现属性而达到的分类器)和显示工件(显示此组件的工件——参见19.3)。

A ComponentRealization is notated in the same way as a Realization dependency (i.e., as a general dashed line with a hollow triangle as an arrowhead).

组件实现的标注方式与实现依赖项(即(如一般虚线与空心三角形作为箭头)。

The packagedElements of a Component may be displayed in an optional compartment named “packaged elements,” according to the specification for optional compartments for ownedMembers set out in 9.2.4.

组件的packagedElements可以显示在一个名为“已打包元素”的可选单元中，这是根据9.2.4中为所有成员设置的可选单元规范实现的。


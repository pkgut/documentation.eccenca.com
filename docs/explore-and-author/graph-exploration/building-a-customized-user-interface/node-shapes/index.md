---
icon: octicons/cross-reference-24
tags:
    - Reference
    - Vocabulary
---
# Node Shapes

Node Shapes are resources of type `shacl:NodeShape`. They are used to define custom forms attached to resources of a specific type. The following NodeShape properties are supported:

In addition to these properties, the following non-standard properties from the eccenca SHACL UI extension are supported on Node Shapes:

#### Naming and Presentation

In this group, presentation and naming properties are collected. Most of the properties are straight forward to use.

##### Name

The name of the node is presented to the user only when he needs to distinguish between different shapes for the same resource.

Used Path: `shacl:name`

##### Description

The node description should provide context information for the user when creating a new resource based on this node.

Used Path: `rdfs:comment`

##### Tab Name (deprecated)

Name of the tab (deprecated, only interpreted until 20.06)

Used Path: `shui:tabName`

##### Navigation list query

This property links the node shape to a SPARQL 1.1 Select Query in order to provide a sophisticated user navigation list query e.g. to add specific additional columns.

Used Path: `shui:navigationListQuery`

#### Vocabulary

In this group, the affected vocabulary classes as well as the used property shapes are managed.

##### Property

Properties of this node

Used Path: `shacl:property`

##### Target class

Class this NodeShape applies to.

Used Path: `shacl:targetClass`

#### Processing

In this group, all shape properties are managed, have an effect on how new or existing resources are processed or created.

##### URI template

A compact sequence of characters for describing a range of URIs through variable expansion.

Used Path: `shui:uriTemplate`

##### On update update

A query executed when any value of the resource is added, changed or removed.

Used Path: `shui:onUpdateUpdate`

##### Target Graph Template

Graph templates can be used to enforce writing statement in specific graphs rather than into the selected graph. Graph templates can be added to node and property shapes. A template on a property shape is used only for overwriting a template on a node shape (without a node shape graph template, they do not have an effect).

Used Path: `shui:targetGraphTemplate`

#### Statement Annotation

Statement Annotations provide a way to express knowledge about statements. This group is dedicated to properties which configure the Statement Annotation feature.

##### Enable

A value of true enables visualisation and management capabilities of statement annotations (reification) for all statements which are shown via this shape.

Used Path: `shui:enableStatementLevelMetadata`

##### Provide as Shape

A value of true enables this node shape to be applied as statement annotation (reification).

Used Path: `shui:isApplicableAsStatementLevelMetadata`


---
layout: post
title:      "MapStateToProps: Store, Components, Props"
date:       2020-07-25 23:04:54 +0000
permalink:  mapstatetoprops_store_components_props
---


React Redux

The library that binds React and Redux together is called React Redux. An essential part of React is the ability to utilize state in a component driven application. The React Redux library expands this capability by providing the process of subscribing to a central local data storage commonly called the store. React Redux incorporates the easy updating of this data and trigger re-renders to make components more reusable. With this in mind, applications utilzing React Redux can be built in a modular component architecture that allows for many small parts to form a whole. This makes the process of debugging, adding features, and expansion easier. 

Managing state in an application

Most modern application utilize state in some way in order to build powerful and dynamic applications, often connected to an API. In general, React utilizes components that manage a local state that re-renders when data is changed. Data is passed from component to component is React with props and state. Props are typically passed from parent component to a child as an attribute and data is passed as is and cannot be mutated. State functions within the local component scope but is only viable during the component's lifecycle. The utilization of React Redux allos for expansion of data passing capabilities and management. 

Redux store

React Redux provide the ability to manage state data in a store container that is accessible to the entire application. Components can access the store to perform actions to manipulate, update, and request data from anywhere within the applications. Another feature of the React Redux library is the store data only changes its state when an action is dispatched and not on each components re-render. This helps to better maintain state and the overall data management.

Mapstatetoprops

Mapstatetoprops is a function provided by the React Redux library that allows application components to share data utilizing props. Once connected to a store, mapstatetoprops can be called to return a plain javascript object or a function that is then merged into the components props and sent to the store. Being able to select specific data allows you to manage the data each component may need, especially if your store has a large amount of data that may not be needed for every component. Also, allows for specific components data to be updated with changes and not the entire store. 

React Redux helps to maintain overall data storage and ensures your components only receive and update the data that is important to each specific component. 

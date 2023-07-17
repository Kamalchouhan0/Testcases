React Testing with Jest and Enzyme
This file guidelines and examples for writing test cases for React components using Jest and Enzyme. It covers both functional and class components.

Unit testing:-
It is an essential and integral part of the software development process that helps us ensure the product’s stability. It is the level of testing at which every component of the software is tested. Testing is required for the effective performance of a software application or product.

Table of Contents
Prerequisites
Installation
Writing Test Cases
Functional Components
Class Components
Running Tests

Prerequisites
Before getting started, make sure you have the following installed:

Node.js (version 12 or higher)
npm (Node package manager)
React (version 16.8 or higher)
Jest (version 27 or higher)
Enzyme (version 3 or higher)

Installation
To install the required dependencies, run the following command in your project directory:

npm install --save-dev jest enzyme enzyme-adapter-react-16

Writing Test Cases
Here we will make two files example.scenario.feature and example.web.steps.tsx .
In example.scenario.feature file we will write diffrent scenarios and diffrent steps which user will face when he/she will login to the app and use the particular feature ,and face the steps written inside scenario.

example.scenario.features
Feature: Example

    Scenario: User navigates to example page
        Given I am a User loading example page
        When I navigate to the example page
        Then example page will load with out errors
        Then example page should be load
        Then I should be able to get alert message is API got failed
        And I can leave the screen with out errors

For Second file we will see how to write test cases for fuctional and class component
The main difference lies in the scope and focus of the test cases. Test cases in a class typically target specific methods or functions within a class, while test cases in a functional component typically encompass the overall behavior and functionality of the component itself.

Functional Components
For funtional components,, we can use Jest and Enzyme's shallow rendering.

import { defineFeature, loadFeature } from "jest-cucumber"
import { mount, shallow, ShallowWrapper } from 'enzyme'
import React from "react";

import { Example } from "../../src/example.web";
const navigation = require("react-navigation")

const screenProps = {
navigation: navigation,
id: "Example",
t: (key: any) => key
}

const feature = loadFeature('./**tests**/features/example-scenario.feature');

defineFeature(feature, (test) => {

    beforeEach(() => {
        jest.resetModules()
        jest.doMock('react-native', () => ({ Platform: { OS: 'web' } }))
        jest.spyOn(helpers, 'getOS').mockImplementation(() => 'web');
    });

    test("User navigates to example page", ({ given, when, then }) => {
        let ExampleBlock: ShallowWrapper;
        let instance: Example;

        given("I am a User loading example page ", () => {
            ExampleBlock = shallow(<Example {...screenProps} />);
        });

        when("I navigate to the example page", () => {
            instance = ExampleBlock.instance() as Example;
        });
        then('example page will load with out errors', () => {
            expect(ExampleBlock).toBeTruthy();
        });
        then('example page should be load', () => {
            instance.componentDidMount();
            instance.getExampleDetails();
            let exampleData: any = {
                requestId: "123kide",
                requestType: "urgent",
                customer: "test",
                customerId: "test123",
            }

                window.localStorage.setItem('exampleData', JSON.stringify(exampleData))
            })

            const msgProductRestAPI = new Message(
                getName(MessageEnum.RestAPIResponceMessage)
            );
            instance.getExampleDetailsAPI = msgProductRestAPI.messageId
            msgProductRestAPI.addData(
                getName(MessageEnum.RestAPIResponceDataMessage),
                msgProductRestAPI.messageId
            );
            msgProductRestAPI.addData(
                getName(MessageEnum.RestAPIResponceSuccessMessage),
                {
                    data: exampleDetails.data
                }
            );
            runEngine.sendMessage("Unit Test", msgProductRestAPI);


        })
        then('I should be able to get alert message is API got failed', () => {
            instance.getExampleDetails()
            const msgLogInErrorRestAPI = new Message(
                getName(MessageEnum.RestAPIResponceMessage)
            );
            msgLogInErrorRestAPI.addData(
                getName(MessageEnum.RestAPIResponceDataMessage),
                msgLogInErrorRestAPI
            );
            msgLogInErrorRestAPI.addData(
                getName(MessageEnum.RestAPIResponceSuccessMessage),
                {
                    errors: [
                        "Something went wrong"
                    ],
                }
            );

            msgLogInErrorRestAPI.addData(
                getName(MessageEnum.RestAPIResponceDataMessage),
                msgLogInErrorRestAPI.messageId
            );
            instance.getExampleDetailsAPI = msgLogInErrorRestAPI.messageId;
            runEngine.sendMessage("Unit Test", msgLogInErrorRestAPI);
        });
        then('I can leave the screen with out errors', () => {
            instance.componentWillUnmount()
            expect(ExampleBlock).toBeTruthy();
        });
    });

Class Components
For class components,, we can use Jest and Enzyme's shallow rendering.

import { defineFeature, loadFeature } from "jest-cucumber"
import { mount, shallow, ShallowWrapper } from 'enzyme'
import React from "react";
import { example } from "../../src/example.web";
const navigation = require("react-navigation")

const screenProps = {
navigation: navigation,
id: "example",
t: (key: any) => key
}

const feature = loadFeature('./**tests**/features/example-scenario.feature');

defineFeature(feature, (test) => {

    beforeEach(() => {
        jest.resetModules()
        jest.doMock('react-native', () => ({ Platform: { OS: 'web' } }))
        jest.spyOn(helpers, 'getOS').mockImplementation(() => 'web');
    });

    test("User navigates to example page", ({ given, when, then }) => {
        let ExampleBlock: ShallowWrapper;
        let instance: Example;

        given("I am a User loading example page ", () => {
            ExampleBlock = shallow(<Example {...screenProps} />);
        });

        when("I navigate to the example page", () => {
            instance = ExampleBlock.instance() as Example;
        });
        then('example page will load with out errors', () => {
            expect(ExampleBlock).toBeTruthy();
        });
        then('example page should be load', () => {
            instance.componentDidMount();
            instance.getExampleDetails();
            let exampleData: any = {
                requestId: "123kide",
                requestType: "urgent",
                customer: "test",
                customerId: "test123",
            }

                window.localStorage.setItem('exampleData', JSON.stringify(exampleData))
            })

            const msgProductRestAPI = new Message(
                getName(MessageEnum.RestAPIResponceMessage)
            );
            instance.getExampleDetailsAPI = msgProductRestAPI.messageId
            msgProductRestAPI.addData(
                getName(MessageEnum.RestAPIResponceDataMessage),
                msgProductRestAPI.messageId
            );
            msgProductRestAPI.addData(
                getName(MessageEnum.RestAPIResponceSuccessMessage),
                {
                    data: exampleDetails.data
                }
            );
            runEngine.sendMessage("Unit Test", msgProductRestAPI);


        })
        then('I should be able to get alert message is API got failed', () => {
            instance.getExampleDetails()
            const msgLogInErrorRestAPI = new Message(
                getName(MessageEnum.RestAPIResponceMessage)
            );
            msgLogInErrorRestAPI.addData(
                getName(MessageEnum.RestAPIResponceDataMessage),
                msgLogInErrorRestAPI
            );
            msgLogInErrorRestAPI.addData(
                getName(MessageEnum.RestAPIResponceSuccessMessage),
                {
                    errors: [
                        "Something went wrong"
                    ],
                }
            );

            msgLogInErrorRestAPI.addData(
                getName(MessageEnum.RestAPIResponceDataMessage),
                msgLogInErrorRestAPI.messageId
            );
            instance.getExampleDetailsAPI = msgLogInErrorRestAPI.messageId;
            runEngine.sendMessage("Unit Test", msgLogInErrorRestAPI);
        });
               then('I can leave the screen with out errors', () => {
            instance.componentWillUnmount()
            expect(ExampleBlock).toBeTruthy();
        });
    });

Running Tests
Jest will automatically detect and run all test files with the .test.js extension in your project directory.
After writing all the test cases for each file we will type the following command to run the test.

yarn run test

This command will test all the scenario steps and the functions written inside it and will give to the percantage of how many branches, functions and lines you have covered in the given tsx file and it should be overall more then 80% to pass the test cases .It will also make a coverage folder in which you can see the leftout functions and lines ,and make your test case percentile incresed .

# cfn-modules: AWS VPC

AWS VPC using two or three availability zones with public and private subnets, VPC endpoints for DynamoDB and S3, Flow Logs, and NAT gateways.

## Install

> Install [Node.js and npm](https://nodejs.org/) first!

```
npm i @cfn-modules/vpc
```

## Usage

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules example'
Resources:
  Vpc:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        AlertingModule: '' # optional
        ClassB: 0 # optional
        NumberOfAvailabilityZones: 3 # optional
        S3Endpoint: true # optional
        DynamoDBEndpoint: true # optional
        FlowLog: 'reject-only' # optional
        FlowLogRetentionInDays: 14 # optional
        NatGateways: true # optional
      TemplateURL: './node_modules/@cfn-modules/vpc/module.yml'
```

## Parameters

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Default</th>
      <th>Required?</th>
      <th>Allowed values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>AlertingModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/alerting">alerting module</a></td>
      <td></td>
      <td>false</td>
      <td></td>
    </tr>
    <tr>
      <td>ClassB</td>
      <td>Class B of VPC (10.XXX.0.0/16)</td>
      <td>0</td>
      <td>no</td>
      <td>[0-255]</td>
    </tr>
    <tr>
      <td>NumberOfAvailabilityZones</td>
      <td>How many availability zones should be used?</td>
      <td>3</td>
      <td>no</td>
      <td>[2-3]</td>
    </tr>
    <tr>
      <td>S3Endpoint</td>
      <td>Add S3 endpoint to VPC?</td>
      <td>true</td>
      <td>no</td>
      <td>[true, false]</td>
    </tr>
    <tr>
      <td>DynamoDBEndpoint</td>
      <td>Add DynamoDB endpoint to VPC?</td>
      <td>true</td>
      <td>no</td>
      <td>[true, false]</td>
    </tr>
    <tr>
      <td>FlowLog</td>
      <td>Enable VPC Flow Logs?</td>
      <td>reject-only</td>
      <td>no</td>
      <td>[true, reject-only, false]</td>
    </tr>
    <tr>
      <td>FlowLogRetentionInDays</td>
      <td>Specifies the number of days you want to retain log events</td>
      <td>14</td>
      <td>no</td>
      <td>[1, 3, 5, 7, 14, 30, 60, 90, 120, 150, 180, 365, 400, 545, 731, 1827, 3653]</td>
    </tr>
    <tr>
      <td>NatGateways</td>
      <td>Add Nat Gateway per private Subnet?</td>
      <td>true</td>
      <td>no</td>
      <td>[true, false]</td>
    </tr>
  </tbody>
</table>

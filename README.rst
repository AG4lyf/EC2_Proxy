=========
EC2 Proxy
=========


.. image:: https://img.shields.io/pypi/v/ec2_proxy.svg
   :target: https://pypi.python.org/pypi/ec2_proxy

.. image:: https://img.shields.io/travis/AG4lyf/ec2_proxy.svg
   :target: https://travis-ci.com/AG4lyf/ec2_proxy

.. image:: https://readthedocs.org/projects/ec2-proxy/badge/?version=latest
   :target: https://ec2-proxy.readthedocs.io/en/latest/?version=latest
   :alt: Documentation Status


This package provides the ability to use Amazon AWS as a proxy with ever-changing IP.


* Free software: Apache Software License 2.0
* Documentation: https://ec2-proxy.readthedocs.io.

Install a Proxy Server
======================
Read
`Setup </proxy_setup.md>`__
for instructions on how to install a proxy server on an EC2 instance.


How to Use
==========
1. Install the package:
      pip install ec2_proxy

2. Create an AWS account and obtain the access key and secret key from 
`Here <https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/security_credentials/access-key-wizard>`__
.


There are 2 ways to use this package:

Way #1 - Use it with the credentials that are present in your `.aws` folder in your home directory

.. code-block:: python

      from ec2_proxy import TProxy

      tp = TProxy(<instance_id_here>)
      ip = tp.start()
      print(ip)

Way #2 - Use it with the credentials that you will pass at runtime

.. code-block:: python

      from ec2_proxy import TProxy
      from botocore.config import Config
      import boto3

      region = 'us-west-2'
      access_key_id = 'YOUR_ACCESS_KEY_ID'
      secret_access_key = 'YOUR_SECRET_ACCESS_KEY'

      ec2 = boto3.client('ec2', region_name=region, aws_access_key_id=access_key_id, aws_secret_access_key=secret_access_key)
      tp = TProxy(<instance_id_here>, ec2=ec2)
      ip = tp.start()
      print(ip)

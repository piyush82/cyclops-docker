# Copyright (c) 2015. Zuercher Hochschule fuer Angewandte Wissenschaften
# All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License"); you may
# not use this file except in compliance with the License. You may obtain
# a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
# WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
# License for the specific language governing permissions and limitations
# under the License.
#
# Author: Piyush Harsh,
# URL: piyush-harsh.info
#
# Thanks to: https://hub.docker.com/_/java/

FROM cyclopsbilling/cyclops-base
EXPOSE 4571

RUN apt-get update
RUN apt-get install -y postgresql-client curl

#creating coin log directories
RUN mkdir -p /var/log/cyclops/ruleengine/
RUN find /var/log/cyclops -type d -exec chmod 755 {} \;
RUN touch /var/log/cyclops/ruleengine/errors.log
RUN touch /var/log/cyclops/ruleengine/trace.log
RUN touch /var/log/cyclops/ruleengine/rules.log
RUN touch /var/log/cyclops/ruleengine/facts.log
RUN touch /var/log/cyclops/ruleengine/dispatch.log
RUN touch /var/log/cyclops/ruleengine/timeline.log
RUN touch /var/log/cyclops/ruleengine/hibernate.log
RUN touch /var/log/cyclops/ruleengine/stream.log
RUN find /var/log/cyclops/ruleengine -type f -exec chmod 666 {} \;

RUN wget https://raw.githubusercontent.com/icclab/cyclops-binaries/master/bin/coin.jar
ADD coin.conf coin.conf
ADD run.sh run.sh
RUN chmod +x run.sh

CMD ["/bin/bash", "run.sh"]
#CMD ["java", "-jar", "coin.jar", "coin.conf"]

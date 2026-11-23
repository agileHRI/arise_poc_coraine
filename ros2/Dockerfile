# Copyright 2026 Seamware
# SPDX-License-Identifier: Apache-2.0
#
# ROS 2 Jazzy (Vulcanexus) with eProsima's keyed turtlesim demo.
FROM eprosima/vulcanexus:jazzy-desktop

RUN git clone --depth 1 --branch jazzy https://github.com/eProsima/vulcanexus.git /tmp/vulcanexus \
 && mkdir -p /ros2-ws/src \
 && mv /tmp/vulcanexus/code/turtlesim /ros2-ws/src/ \
 && rm -rf /tmp/vulcanexus

WORKDIR /ros2-ws
RUN bash -c "source /opt/vulcanexus/jazzy/setup.bash && colcon build"

RUN echo "source /ros2-ws/install/setup.bash" >> /root/.bashrc

CMD ["sleep", "infinity"]

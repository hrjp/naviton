FROM hrjp/naviton:melodic_cudagl

RUN cd /home && \
    git clone https://github.com/hrjp/rosenv && \
    ./rosenv/naviton_package.bash && \
    ./rosenv/hdl_install.bash
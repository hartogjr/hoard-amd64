# BSD 3-Clause License
#
# Copyright (c) 2022-2023, Bren de Hartog <bren@dehartog.name>
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
# 1. Redistributions of source code must retain the above copyright notice, this
#    list of conditions and the following disclaimer.
#
# 2. Redistributions in binary form must reproduce the above copyright notice,
#    this list of conditions and the following disclaimer in the documentation
#    and/or other materials provided with the distribution.
#
# 3. Neither the name of the copyright holder nor the names of its
#    contributors may be used to endorse or promote products derived from
#    this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
# FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
# SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
# CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
# OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

add_library (hoard SHARED
	libhoard.cpp
	unixtls.cpp
)

target_compile_options (hoard
	PRIVATE
		-flto -Wall -Wextra -ffast-math -fno-builtin-malloc -Wno-shadow
		-Wno-conversion -Wno-uninitialized -D_REENTRANT=1 -Wno-sign-compare
		-Wno-unused-variable
)

target_link_options (hoard
	PRIVATE
		-flto
)

target_compile_features (hoard PUBLIC cxx_std_14)

target_include_directories (hoard
	PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/../inc
	${CMAKE_CURRENT_SOURCE_DIR}/../inc/util
	${CMAKE_CURRENT_SOURCE_DIR}/../inc/hoard
	${CMAKE_CURRENT_SOURCE_DIR}/../inc/superblocks
)

target_link_libraries (hoard
	PRIVATE
		Threads::Threads
)

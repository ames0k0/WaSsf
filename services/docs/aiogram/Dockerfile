FROM alpine:latest

WORKDIR /aiogram

RUN apk add --no-cache git
RUN apk add --no-cache python3 py3-pip
RUN apk add --no-cache py3-sphinx-autobuild
RUN apk add --no-cache py3-sphinxcontrib-serializinghtml

RUN git clone \
	--single-branch \
	--no-tags \
	--depth=1 \
	https://github.com/aiogram/aiogram.git \
	.

RUN pip install --break-system-packages .
# FIXFOR
# - No module named 'sphinx_substitution_extensions'
# - No module named 'sphinx_copybutton'
RUN pip install --break-system-packages Sphinx-Substitution-Extensions sphinx-copybutton

EXPOSE 8989

CMD ["sphinx-autobuild", "--watch", "aiogram/", "docs/", "docs/_build/", "--port", "8989"]

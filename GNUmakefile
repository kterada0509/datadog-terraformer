TEST?=./...
GOFMT_FILES?=$$(find . -name '*.go' |grep -v vendor)
VERSION?=$$(git describe --abbrev=0 --tags)
BUILDDATE?=$$(date '+%Y/%m/%d %H:%M:%S %Z')
HASH?=$$(git rev-parse --verify HEAD)
GOVERSION?=$$(go version)

export GO111MODULE := on

default: fmt

# Install all the build and lint dependencies
setup:
	go mod download
.PHONY: setup

fmt:
	@echo "==> Fixing source code with gofmt..."
	gofmt -s -w ./

# Currently required by tf-deploy compile
fmtcheck:
	@sh -c "'$(CURDIR)/scripts/gofmtcheck.sh'"

errcheck:
	@sh -c "'$(CURDIR)/scripts/errcheck.sh'"

vendor-status:
	@govendor status
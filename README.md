Changes to types within `node_modules` do not invalidate the TypeScript build output.

1. `yarn tsc -b tsconfig.soln.json`. Notice that no errors are reported.
2. Make some modification to `node_modules/@types/lodash` that would cause an error in the project.
   For example, edit `node_modules/@types/lodash/ts3.1/common/util.d.ts:881` to accept a `string` instead of a `number`.
   This is meant to simulate an update to the types within `node_modules`.
3. `yarn tsc -b tsconfig.soln.json`. Notice that no errors are reported. This is unexpected.
4. `rm -rf build && yarn tsc -b tsconfig.soln.json`. Notice that errors we expected in step 3 are reported.
5. Unto the edit made in step 2.
6. `yarn tsc -b tsconfig.soln.json`. Notice that no errors are reported, as expected.

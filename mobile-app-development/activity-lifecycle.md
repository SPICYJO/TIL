# Activity Life Cycle

## State
- Initialized
- Destroyed
- Created
- Started: Activity is visible
- Resumed: Activity has focus

## overridable methods
- `onCreate()`: Initialized -> Created
- `onStart()`: Created -> Started
- `onRestart()`: Created -> Started
- `onResume()`: Started -> Resumed
- `onPause()`: Resumed -> Started
- `onStop()`: Started -> Created
- `onDestroy()`: Created -> Destroyed

- `onRestoreInstanceState()`: After `onCreate()`
- `onSaveInstanceState()`: After `onStop()`
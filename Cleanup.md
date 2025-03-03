mkdir grep_results
grep -r 'Decimal("0")' src/ -n --include=\*.py > grep_results/silent_zeros.txt
grep -r 'create_decimal("0")' src/ -n --include=\*.py >> grep_results/silent_zeros.txt
grep -r 'except.*pass' src/ -n --include=\*.py > grep_results/silent_passes.txt
grep -r 'except Exception.*pass' src/ -n --include=\*.py >> grep_results/silent_passes.txt
grep -r 'return {}' src/ -n --include=\*.py > grep_results/weak_dicts.txt
grep -r 'return None' src/ -n --include=\*.py > grep_results/weak_nones.txt
grep -r 'return Decimal("0")' src/ -n --include=\*.py > grep_results/weak_zeros.txt
grep -r 'except.*return' src/ -n --include=\*.py | grep -v 'raise' | grep -v 'logger' > grep_results/sneaky_returns.txt
grep -r 'AsyncMock' tests/ -n --include=\*.py > grep_results/mock_async.txt
grep -r 'MagicMock' tests/ -n --include=\*.py > grep_results/mock_magic.txt
grep -r 'except Exception' src/ -n --include=\*.py > grep_results/broad_excepts.txt
